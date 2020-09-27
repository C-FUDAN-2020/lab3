# lab3

    本节目标：

      1、熟悉C语言中输入输出语句
      2、熟悉C语言中数据类型
      3、编写一个简单的加减乘除运算的C程序
      4、编写一个格式化打印的C程序
     
     


## 获取及提交lab
获取：通过 `https://github.com/C-FUDAN-2020/lab3`，获取（建议通过Download ZIP方式下载）。

提交物：将你完成目标3和目标4的源代码文件作为 lab3 的提交物。

提交：将提交物文档命名为学号_姓名 （如20302010000_王明），提交至超星学习通对应的作业中。

截止时间：北京时间 `2020年10月04日 23:59:59`


## 熟悉C语言中输入输出语句

### * printf函数
`printf 函数`的调用格式为：

    printf("<格式化字符串>", <参量表>);
    
<格式化字符串>为将被输出的字符串模板，字符串内部可以插入类似%d,%f的变量占位符。占位符在输出时将被替换为<参量表>内对应的变量。需要注意，有几个占位符就需要几个传入参数。

例如：

    int main()
    {
        int a = 0, b = 1;
        float c = 1.5;
        printf("a=%d,b=%d,c=%f\n",a,b,c);
       return 0;
    }
    
上面的程序将输出a=0,b=1,c=1.500000。

占位符支持的格式为：
         
     %[标记][字符串总长度][.浮点数精度][格式字符长度]
     
格式字符，下面介绍基本用法。`格式字符需要与传入的参数类型保持一致`，下面是常见类型参数：

     格式字符	               意义
       d	    以十进制形式输出带符号整数(正数不输出符号)
       u	        以十进制形式输出无符号整数
       f	       以小数形式输出单、双精度实数
       c	               输出单个字符
       s	                输出字符串
       p	               输出指针地址

`标记支持`为字符串的输出时改变输出格式。例如，使用-将字符串左对齐（默认右对齐），使用+输出变量的符号。

`字符串总长度`指定变量的最小长度，如果变量小于这个值，将用空格填充。

`浮点数精度`指定输出浮点数的精度，如果输入小于精度，将以0填充，默认小数输出时的精度为6。

下面的程序指定浮点数a输出精度为3：

      int main()
      {
           float a = 1.23456f;
           printf("a=%.3f\n",a);/* 这里将打印a=1.235 */
           return 0;
      }

同学们如果想更加深入了解printf函数，请查阅[这里](https://www.runoob.com/cprogramming/c-input-output.html)。

### * scanf函数

C语言中我们经常使用 scanf 接收控制台的输入。

`scanf函数` 的调用格式为：

     scanf("<格式化字符串>", <参量表>);

`与 printf 的区别为 scanf 传入的参数为变量的指针`。现在我们不需要大家了解指针的概念，这里解释一下使用指针的原因。scanf 需要修改变量的值为输入的值，所以需要传入指针而不是变量的值。所以请大家明确：&varible != varible 。

接下来举一个例子：

    int main()
    {
       int a;
       float b;
       scanf("%d %f",&a,&b);/* 中间的分隔符可以自由使用，一般用空格 */
       printf("a=%d, b=%.2f\n",a,b);
       return 0;
    }
   
同学们如果想更加深入了解scanf函数，请查阅[这里](https://www.runoob.com/cprogramming/c-input-output.html)。

## 熟悉C语言中数据类型

在 C 语言中，`数据类型指的是用于声明不同类型的变量或函数的一个广泛的系统`。变量的类型决定了变量存储占用的空间，以及如何解释存储的位模式。

C 中的数据类型可分为以下几种：

     序号	                                类型与描述
      1	           基本类型：它们是算术类型，包括：整数类型，浮点类型和字符类型。
      2	   枚举类型：它们也是算术类型，被用来定义在程序中只能赋予其一定的离散整数值的变量。
      3	                 void 类型：类型说明符 void 表明没有可用的值。
      4	      派生类型：它们包括：指针类型、数组类型、结构类型、共用体类型和函数类型。

数组类型和结构类型统称为聚合类型。函数的类型指的是函数返回值的类型。下面简单介绍几种基本数据类型。

### * 整数类型
下表列出了关于标准整数类型的存储大小和值范围的细节：

       类型	           存储大小	                                  值范围
       char	             1 字节	                     -128 到 127 或 0 到 255
    unsigned char  	     1 字节	                              0 到 255
    signed char              1 字节	                            -128 到 127
       int	           2 或 4 字节	        -32,768 到 32,767 或 -2,147,483,648 到 2,147,483,647
    unsigned int	   2 或 4 字节	               0 到 65,535 或 0 到 4,294,967,295
      short	             2 字节	                         -32,768 到 32,767
    unsigned short	     2 字节	                            0 到 65,535
       long	             4 字节	                   -2,147,483,648 到 2,147,483,647
    unsigned long	     4 字节	                       0 到 4,294,967,295
    
### * 浮点类型

下表列出了关于标准浮点类型的存储大小、值范围和精度的细节：

        类型	    存储大小	      取值范围	            精度
       float	      4 字节	    1.2E-38 到 3.4E+38	        6 位小数
       double	      8 字节	    2.3E-308 到 1.7E+308	        15 位小数
     long double      16 字节	   3.4E-4932 到 1.1E+4932	19 位小数
     
### * 字符类型

char类型用于表示单个字符或转义字符。字符类型值必须使用`单引号`括起来。




##### 提醒：这三种基本数据类型只是粗浅介绍，请同学们在课后进行系统和全面地学习。其他数据类型的学习也请同学们在课后自主认真地学习。

在这里举一个例子：

    #include<stdio.h>
    int main()
     {
	   int m,n;
	   char ch[10],ch1,ch2;
	   scanf("%d",&m);
	   scanf("%c",&ch1);
	   scanf("%s",ch);/* ch对于用户而言是数组名，对计算机而言是数组的首地址，此处可以不加*& */ 
	   scanf("%c",&ch2);
	   printf("%d %d %s %d\n",m,ch1,ch,ch2);	
	   return 0;
     }
 
 上述程序输入为45 yuyan，输出为45 32 yuyan 10。


## 编写一个加减乘除运算的C程序

编写一个C程序，求一个圆的面积。键盘输入圆的半径，输出圆的面积（π取3.14）。

举例，如
 
     输入：圆的半径为6
 
     输出：圆的面积为113.04
     
## 编写一个格式化打印的C程序

编写一个C程序，按照如下图输出。`（本lab为简化版生命游戏的界面，字符“*”表示无生命，字符“#”表示有生命，注意输出的格式。）`
     
      
        *  *  *  *  *  *  *
        *  *  #  #  #  *  *
        *  *  #  #  #  *  *
	*  *  #  #  #  *  *
	*  *  *  *  *  *  *
	
        
 补充一个本题需要用到的知识点，`部分转义字符`和其所对应的意义：
         
    转义字符            意义
     \a              响铃(BEL)
     \b     退格(BS) ，将当前位置移到前一列
     \f     换页(FF)，将当前位置移到下页开头
     \n     换行(LF) ，将当前位置移到下一行开头
     \r     回车(CR) ，将当前位置移到本行开头
     \t     水平制表(HT) （跳到下一个TAB位置）
     \\     代表一个反斜线字符''\'
     \'     代表一个单引号（撇号）字符
     \"     代表一个双引号字符
     \?	    代表一个问号
     \0     空字符(NUL)

## Reference
[1][https://www.runoob.com/cprogramming/c-input-output.html](https://www.runoob.com/cprogramming/c-input-output.html)

[2][https://www.runoob.com/cprogramming/c-data-types.html](https://www.runoob.com/cprogramming/c-data-types.html)
