# 第一章 开始
## 01.编写一个简单的C++程序
每个C++程序都包含一个或多个函数（function）,其中一个必须命名为main,一个函数的定义包括：   
  * 返回类型（return type）   
  * 函数名（function name）  
  * 参数列表（parameter list，允许为空）   
  * 函数体（function body）  
```c
int main(int argc, char *argv[]) //C
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

```shell
cin可以跳过空格、制表符、换行符等空白字符
```



