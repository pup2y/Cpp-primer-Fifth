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
double隐式转换为int————>近似处理，截断小数点后部分  
赋给无符号类型一个超出它表示范围的值后，结果是初始值对无符号类型数值总数取模后的余数
当前值 = k * 范围总数 + 余数 (mod)  
赋给有符号类型一个超出它表示范围的值时，结果是未定义的，可能崩溃、继续工作、也可能生成垃圾数据




