# 第二章 变量和基本类型
## 01.基本内置类型
 * C++是一种:blush:**静态**:blush:数据类型语言，在编译时进行类型检查
 * C++定义了：算术类型、空类型
   
![](https://github.com/pup2y/Cpp-primer-Fifth/blob/main/img/002.png)
```diff
+ 计算机以比特序列存储数据，每个比特非0即1,
+ 可寻址的最小内存块称为“字节（byte）”，内存的基本单元称为“字（word）”
+ 大多数机器的字节由8比特构成，字则由32或64比特构成
1 byte = 8 bit 
```

无符号类型  
 * int、short、long和long long都是带符号的，前面加上unsigned就可以得到无符号类型，例如unsigned long
 * unsigned int可以缩写成unsigned。
 * char比较特殊，类型分为三种：char、signed char、unsigned char

## 02.类型转换
* 非布尔类型————>布尔类型时，初始值为0则结果为false，否则结果为true  
* 布尔类型————>非布尔类型时，初始值为false则结果为0，初始值为true则结果为1  
* 浮点型————>整数型时，近似处理，截断小数点后部分  
* 整数型————>浮点型时，小数部分记为0  
* 赋给无符号类型一个超出它表示范围的值后，结果是初始值对无符号类型数值总数取模后的余数   
当前值 = k * 范围总数 + 余数 (mod)  
* 赋给有符号类型一个超出它表示范围的值时，结果是未定义的，可能崩溃、继续工作、也可能生成垃圾数据  

```cpp
bool b=42;		//b为真
int i=b;		  //i的值为1
i=3.14;		 //i的值为3（浮点型转整型）
double pi=i;		//pi的值为3.0
unsigned char c=-1;	//假设char占8比特，c的值为255
//char占8bit,表示范围为0-255，(-1 = -1 * 256 + 255)/(c=-1%256+256) c的值为255  
signed char c2=256;	//假设char占8比特，c2的值未定义
```

## 03.无符号类型表达式
* 当一个算术表达式中既有无符号又有int值时，int值就会转换成无符号数，算术表达式的类型为无符号  
```cpp
unsigned u=10;
int i=-42;
std::cout << i+i << std::endl;//输出-84
std::cout << u+i << std::endl;//如果int占32位，i转换为2^32-42，输出2^32-42+u=4294967264
```
* 字面值常量  一个型如42的值被称为字面值常量（literal）  
* 将整形写成十进制、八进制或十六进制       
```diff
20/*十进制*/  024/*八进制*/  0x14/*十六进制*/
```
* 字符和字符串字面值  
```diff
//编译时加上一个空字符'\0'，实际长度比显示内容多1
'a' //字符字面值 
"Hello World" //字符串字面值
```
* 转义序列  
![](https://github.com/pup2y/Cpp-primer-Fifth/blob/main/img/003.png)
* 泛化的转义序列，其形式是\x后紧跟1个或多个十六进制的数字，或后面紧跟1、2或3个八进制的数字。  
![](https://github.com/pup2y/Cpp-primer-Fifth/blob/main/img/004.png)

## 04.变量
变量：具有类型、具有名称、可操作的存储空间。
* 类型决定了变量所需要的内存空间、布局方式、以及能够表示值的范围。（对于C++而言，变量（variable）和对象（object）一般是可以互换的。）
### 初始化
* 赋值初始化和列表初始化
```cpp
//赋值初始化 
int units_sold = 0;
//列表初始化
int units_sold = {0};
int units_sold{0};
int units_sold(0);
```
注：使用列表初始化时，初始值存在丢失信息的风险，则编译器将报错。  
* 默认初始化
如果定义变量没有定义初始值，则变量被赋予默认值。
  * 内置类型：函数体外初始化为0，函数体内其值未被定义
  * 类的对象：由类决定 
### 声明和定义
声明：声明是用来告诉编译器变量的名称和类型，而不分配内存。   
定义：给变量分配内存，**可以**:kissing:为变量赋初值。  
* 注：通常变量的定义和声明是同时发生的，注意：extern 变量类型 变量名 仅是声明。变量能且只能定义一次，但可以被声明多次。
```cpp
extern int i;// 声明i而非定义i
int j;// 声明并定义j
```
### 标识符
C++标识符（identifier）由字母、数字和下划线组成，其中必须以字母或下划线开头。标识符的长度没有限制，但对大小写敏感。  
且不能与:sleeping:**C++关键词**和:sleeping:**操作符**替代名同名。  
### 作用域
* C++中大多数作用域都以花括号分隔。
* 同一个名字如果出现在程序的不同位置，也可能指向不同的实体。块作用域的局部变量会覆盖掉全局同名变量
* 名字的有效区域始于名字的声明语句，以声明语句所在的作用域末端为结束。
```cpp
#include <iostream>
int reused = 42;  // reused 拥有全局作用域
int main()
{
int unique = 0; // unique 拥有块作用域
// output #1: 42 0
std::cout << reused << " " << unique << std::endl;   

int reused = 0; // 同名的新建局部变量，覆盖了全局变量

// output #2:  0 0
std::cout << reused << " " <<  unique << std::endl;  
// output #3: 显式地访问全局变量，打印 42 0
std::cout << ::reused << " " <<  unique << std::endl;  

return 0;
}
```

## 05.引用
引用：为对象起的别名，**没有内存空间**   
* 定义引用时，把引用和它的初始值绑定在一起，而不是将初始值拷贝给引用。
* __因此无法令引用重新绑定到另外一个对象。__ __因为引用必须初始化。__
```cpp
//每个引用标识符都必须以符号&开头
int ival = 1024;
int &refVal = ival;//refVal指向ival(是ival的另一个名字)
int &refVal2;//报错：引用必须初始化
```

## 06.指针
指针：对地址的封装，本身就是一个**对象**
* 在块作用域内定义的指针若未被初始化，将存放一个不确定值  
* 声明指针变量时，每个变量前都必须有符号* 
* 指针存放某个对象的地址，获取地址需要使用取地址符&
* 指针指向一个对象，需要使用解引用符&访问对象
```cpp
// 定义多个指针变量
int *ip1, *ip2;//ip1和ip2都是指向int型对象的指针

//使用取地址符（运算符&）获取指针所封装的地址
int ival = 42;
int *p = &ival;//p是指向ival的指针

//使用解引用符（运算符*）利用指针访问对象
int ival = 42;
int *p = &ival;//p是指向ival的指针
std::cout<<*p ;//输出42
*p=0;
std::cout<<*p; //输出0
```
### 空指针
空指针：不指向任何对象 
```cpp
int *p1 = nullptr; //C++11
int *p2 = 0;
int *p3 = NULL; //需要#include cstdlib
```
### void *指针
void *指针：纯粹的地址封装，与类型无关。可以用于存放任意对象的地址。 
```cpp
double obj = 3.14, *pd = &obj;
void *pv = &obj;
pv = pd;
```
### 指向指针的指针
* 通过*的个数可以区分指针的级别。
* **表示指向指针的指针。 ***表示指向指针的指针的指针。
```cpp
int ival = 1024;
int *pi = &ival;
int **ppi = &pi;//ppi指向一个int型的指针
```
### 指针的引用
指针是对象，可以定义引用。  
* 离变量名最近的操作符对变量的类型有最直接的影响。
* （int *&r，&离变量名最近，**r是一个引用，声明符的其他部分决定r引用的类型**，int *决定r引用的是一个int指针）
```cpp
int i = 1024;
int *p;
int *&r = p; //r是一个对指针p的引用

r = &i;//r指向i，p指向i
*r = 0;//通过r即p改变i的值为0
```

## 07.const限定符
使用const对变量的类型加以限定，变量的值不能被改变。  
const对象一旦创建后其值就不能再改变，const对象必须初始化（其他时候不能出现在等号左边）。  
```cpp
const int i = get_size(); //正确：运行时初始化
const int j = 42; //正确：编译时初始化
const int k; //错误：k是一个未经初始化的常量

//file_1.cc定义并初始化了一个常量，该常量能被其他文件访问，添加extern关键词
extern const int bufSize = fcn();
```
### const的引用
const的引用————>对常量的引用,**不能被用作修改其绑定的对象**
```cpp
const int ci = 1024;
const int &r1 = ci; //正确：引用及其绑定的对象都是常量
```
* 允许一个常量引用绑定非常量的对象，字面值，或者一般表达式（const int&常量 = 非常量）    
* 不能为一个非常量引用绑定一个常量对象———>:scream:**存在通过非常量引用改变常量对象的风险**
```cpp
int i = 42;
//允许一个常量引用绑定非常量的对象
const int &r1 = i; //正确：i依然可以通过其他途径修改
const int &r2 = 42;
const int &r3 = r1*2;
//不能为一个非常量引用绑定一个常量对象
int &r4 = r1*2; //错误
```   
### 指针和const
1.指向常量的指针（pointer to const）
```cpp
//存放常量对象的地址
const double pi = 3.14;
const double * cptr = &pi;
//例外：指向常量的指针允许指向一个非常量对象
double dval = 3.14;
cptr = &dval; //正确：但不能通过该指针cptr修改非常量dval的值
```
2.常量指针（const指针/const pointer）   
* 指针本身就是常量，不变的是指针本身的值，而非指向的那个值
* 把*放在const之前，说明指针是一个常量 (类型 *const)
```cpp
int errNumb = 0;
int *const curErr = &errNumb;  //常量指针
const double pi = 3.14159;
const double *const pip = &pi;//指向常量的常量指针

*curErr = 0; //正确：可以修改变量errNumb
*pip = 2.71;//错误：不能通过指向常量的指针pip修改常量pi
```
### 顶层const与底层const












