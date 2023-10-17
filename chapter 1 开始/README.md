# 第一章 开始
## 01.编写一个简单的C++程序
每个C++程序都包含一个或多个函数（function）,其中一个必须命名为main,一个函数的定义包括：   
  * 返回类型（return type）   
  * 函数名（function name）  
  * 参数列表（parameter list，允许为空）   
  * 函数体（function body）  
```cpp
 * 返回类型 函数名（参数列表）  //Cpp
 *{
 *   函数体
 *          }

int main() 
{
	return 0; 
}
```

## 02.初始输入输出
iostream库包含两个基础类型istream和ostream。
 * stream（流）：一个流就是一个字符序列，是从IO设备流出或写入IO设备的，“流”主要表达的是，随着时间的推移，字符是顺序生成或消耗的。  
 * istream：input stream，输入流
 * ostream：output stream，输出流

标准库定义了4个IO对象：  
 * cin：istream类型的对象，标准输入（standard input）
 * cout：ostream类型的对象，标准输出（standard output）
 * cerr： ostream类型的对象，标准错误（standard error）
 * clog： ostream类型的对象，用来输出程序运行时的一般信息

```diff
cin可以跳过空格、制表符、换行符等空白字符
```

## 注释简介
C++中有两种注释：    
 * 单行注释  
   //  
 * 界定符对注释  
   /*   
	         */    
   - 不能嵌套

## 03.控制流
### while语句
 * 反复执行一段代码，直至给定条件为假为止。
```cpp
#include <iostream>
int main(){
int sum = 0, val = 1;
//只要val的值小于等于10，while循环就会持续执行
while (val <= 10) {
sum += val;//复合运算符，将sum+val赋予sum
++val;//前缀递增运算符，将val加1
}
std::cout << "Sum of 1 to 10 includsive is "<< sum << std::endl;
return 0;
}
```
### for语句
 * for语句的出现就是为了简化循环这一过程。  
  	结构：初始化语句、循环条件、循环体、表达式
 ```cpp
#include <iostream>
int main(){
int sum = 0;

for (int val = 1; val <= 10;++val) 
	sum += val;//等价于sum=sum+val

std::cout << "Sum of 1 to 10 includsive is "<< sum << std::endl;
return 0;
}
 ```
### if语句
 * if(循环条件) 表达式
```cpp
if (val == currVal)  ++cnt;
else {
std::cout << currVal << " occurs "<< cnt << " times" << std::endl;
currVal = val;//记住新值
cnt = 1;//重置计数器
		}
```

## 04.类
通过类（class）来定义自己的数据结构，一个类定义了一个类型，以及与其相关联的一组操作。     
成员函数（member function）是定义为类的一部分的函数，有时也被称为方法（method）。    







