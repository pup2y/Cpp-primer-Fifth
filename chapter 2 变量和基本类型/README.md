# 第二章 变量和基本类型
## 01.基本内置类型
 * C++是一种:blush:静态:blush:数据类型语言，在编译时进行类型检查
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
* 当一个算术表达式中既有无符号又有int值时，int值就会转换成无符号数 算术表达式的类型为无符号  
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
'a’ //字符字面值
"Hello World“ //字符串字面值
```
* 转义序列  
![](https://github.com/pup2y/Cpp-primer-Fifth/blob/main/img/003.png)
* 泛化的转义序列，其形式是\x后紧跟1个或多个十六进制的数字，或、后面紧跟1、2或3个八进制的数字。
![](https://github.com/pup2y/Cpp-primer-Fifth/blob/main/img/004.png)






