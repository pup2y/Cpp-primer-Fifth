# 第二章 变量和基本类型
## 01.基本内置类型
 * C++是一种:blush:静态:blush:数据类型语言，在编译时进行类型检查
 * C++定义了：算术类型、空类型
   
![](https://github.com/pup2y/Cpp-primer-Fifth/blob/main/Picture/2.png)
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
i=3.14;		 //i的值为3（近似处理）
double pi=i;		//pi的值为3.0
unsigned char c=-1;	//假设char占8比特，c的值为255
//char占8bit,表示范围为0-255，(-1 = -1 * 256 + 255)/(c=-1%256+256) c的值为255  
signed char c2=256;	//假设char占8比特，c2的值未定义
```



