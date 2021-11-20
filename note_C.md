

## printf, sacanf 语句

```c
include <stdio.h>
int main(){
    int a = 0
    printf("give me %d\n",a); //\n是换行
    scanf("%d %d",&a,&b);
}
```

```c
printf("%4d",3);
说明该数字应该占据4个字符的位置，如果不够就在左边补空格。

printf("%-4d",3);
说明该数字应该占据4个字符的位置，如果不够就在右边补空格。
printf("%10.3f",3.2234);
占据10个位置，保留3位小数（四舍五入）
```

用逗号后面的变量来代替%d。

对于scanf,在控制台输入的内容必须和引号里的一模一样，否则就不能正确读取信息。之后通过&指向被赋值的数。如果要输入不同类型的内容。

```c
scanf("%d%c",&i,&c);
这时如果输入“23 a“ 那么c 就会被赋值成空格' '  
```

### 逃逸字符

|   字符  |     意义    |
| :---: | :-------: |
|  \\b  | backspace |
|  \\t  |    tab    |
|  \\n  |     换行    |
|  \\'  |     '     |
|  \\"  |     "     |
| \\ \\ |     \\    |

## 数据类型

-   整数

    -   int a = 5
    -   printf("%d
    -   scanf("%d
    -   运算的结果如果不是整数，则直接省略小数点之后所有的东西 

-   双精度浮点数：

    -   double b = 3.4
    -   printf("%f
    -   scanf("%lf

-   单个字符
    -   char ch = '#';
    -   printf("%c",ch);
    -   也可以用%d输出，值为ASCII码的值

-   字符串
    -   char name\[]="Jack"
    -   printf("%s", name)

-   地址
    -   int \*p,\*q;
    -   p = &i;
    -   printf("%p",p);
    -   printf("%d",\*p);

对于不变量，可以使用const，且通常用大写字母表示:

```c
const int RATE = 9;
const double STANDARD = 1.09;
```

## 运算符

```c
    count++
    count += 1
    count = count + 1
```

三者的意思是相同的。特别地，a++是a原来的值，++a是a加一之后的值。但是只要你输入了a++. ++a，那这个操作一定会被执行。

### 比较运算符

比较运算符有"=="!="&lt;">"&lt;=">="几种。当他们为真时，计算结果为1，否则为0。同时，他们的运算优先度小于计算符，但是大于赋值的等于号。

### 逻辑运算符

-   && : 与
-   || : 或
-   ! ：非

他们只能对 0, 1 做运算。对于非 0 整数都当做1。当 && 的左边已经是false ，或 || 的左边已经是 ture, 符号右边的就不会再做运算。

### 优先级

| 优先级 |       运算符       |  运算方向 |
| :-: | :-------------: | :---: |
|  1  |       ( )       |   →   |
|  2  |   ! + - ++ --   | ←（单目） |
|  3  |      \* / %     |   →   |
|  4  |       + -       |   →   |
|  5  | &lt; > &lt;= >= |   →   |
|  6  |      == !=      |   →   |
|  7  |        &&       |   →   |
|  8  |       \|\|      |   →   |
|  9  |  = += -= \*= /= |   ←   |

## 判断语句

### if-else 语句

```c
#include <stdio.h>
int main(){
    int score;
    printf("Please enter your score ");
    scanf("%d", &score);
    
    printf("your score is %d\n",score);
    
    int min = 60;
    
    if(score<min){
        printf("you failed the exam.\n");
    }else{
        printf("you passed the exam.\n");
    }
    printf("Goodbye!\n");
    
    return 0;
}
```

if, else语句的大括号中间若存在多个语句，每个语句中间都需要加分号。同时，若if, else语句后只需要执行一个命令，则可去掉大括号，使用下面的写法：

```c
if(a < b)
    max = b;
else
    max = a;
return 0
```

### 另一种写法

```c
count = (count > 20) ? count - 10 : count + 10;

==

if (count > 20){
    count =  count - 10;
}else{
    count = count + 10;
}
```

### 级联的if, else if

```c
if(x<=0){
    f = 0;
}else if(x<=5){
    f = x * x;
}else if(x<= 100){
    f = x - 90;
}else {
    f = 1;
}
```

### switch-case

```c
int type 
    
switch (type){
    case 0 :
    case 1 :
        a++;
        printf("xxx");
        break;
        
    case 100 :
        a *= 100;
        printf("100");
    
    case 10+39 :
        b = 100;
        break;
        
    default:
        printf("good bye!");
}
```

当进入switch时，if(type==n) 就会跳到case n 那里。

case 仅仅是一个路标，如果没有遇到 break，则指令仍会继续执行，包括 default, 直到 switch 函数结束为止。

## 循环语句

循环语句通常有三种函数：while, do-while, for

-   while

```c
#include <stdio.h>
int main(){
    int n= 1;
	int d;
	scanf("%d",&d);
	d/=10;
  
	while(d!=0){
		n++;
		d/=10;
	}
	printf("%d\n",n);
	return 0;
} 
```

-   do-while

当至少需要循环一次的时候，通常会使用do-while 循环

```c
#include <stdio.h>
int main(){
	int n= 0;
	int d;
	scanf("%d",&d);
    
    do{
        n++;
        d/=10;
    }while(d!=0);
	
	printf("%d\n",n);
	return 0;
} 
```

-   for

for 循环的格式通常为 for( i = 初始; 条件; 每次循环需要做的)。同时，i 必须要在for 的外面定义。

```c
	scanf("%d",&n);
	int i
	for(i=2; i<=n; i++){
		solution*=i;
	}
	printf("n!=%d\n",solution);
```

其中，分号隔开的内容可以省略。例如：

```c
for(;i!=30;) == while(i!=30)
```

在我们想要中途离开循环时，可以利用 break 和 continue.

break: 直接结束循环
continue: 结束这一次循环，从循环的开头再继续执行。

对于多重循环，我们有两种手段可以直接跳出循环。

第一种为break 接力。即定义一个exit 变量，想要退出时令exit = 1即可

```c
	int one,two,five;
	int x; 
	scanf("%d",&x);
	int exit = 0;
	
	for(one = 1; one < x* 10 ; one ++){
		for(two = 0; two < x*10/2; two ++){
			for (five = 0 ; five < x*10/2 ;five ++){
				if (one+two*2 + five * 5 == x * 10){
					printf("one = %d, two = %d, five = %d\n",one,two,five);
					
					exit = 1;
					break;
				}
			}if (exit ==1)break;
		}if (exit ==1)break;
	}
	return 0;
} 
```

另一种是使用goto 函数，跳到任意位置即可。

```c
	int one,two,five;
	int x; 
	scanf("%d",&x);
	
	
	for(one = 1; one < x* 10 ; one ++){
		for(two = 0; two < x*10/2; two ++){
			for (five = 0 ; five < x*10/2 ;five ++){
				if (one+two*2 + five * 5 == x * 10){
					printf("one = %d, two = %d, five = %d\n",one,two,five);
					
					
					goto out;
				}
			}
		}
	}
	out:
    return 0
}
```

## 函数

-   函数的声明

我们可以在main 函数的前面写一个函数的头来声明函数的类型（是int, double, void）,以及输入的类型，最后加分号。然后在main 函数之后补全它的内容。

如果（）里什么都不写，那么在引用的时候默认输入的值为int.
如果函数的类型不写，那么也默认为int。

在声明函数的时候可以不用写变量的名字 (begin , finish)，但是引用和main函数之后不全函数的时候要写。

```c
int sum(int begin, int finish);
    
```

-   函数体

如果为void 函数，那么不可以return 任何一个东西。（可以只写 return; ）
如果函数有输出，那么就必须在 return 之后输入正确类型的数据。

## 数组

一个数组的经典的应用（计数器）

```c
#include <stdio.h>
int main(){
	const int number = 10;
	int count[number];
	int i;
	int x;
	
	for(i=0;i<number;i++){
	
		count[i]=0;
	}
		
	scanf("%d",&x);
	while (x!= -1){
		if(x>=0&&x<=9){
			count[x]++;
		}
		scanf("%d",&x);
	} 
	
	for (i=0;i<10;i++){
	printf("%d: %d ",i,count[i]);
	}	
	return 0;
} 
```

### 数组的初始化

对于多维数组，我们通常有几种初始化方式：

```c

int a[][5] = {
    {1,2,3,4,}
    {2,3,4,5,6,}
}
```

其中，每一行可以不填满，表示行分割的大括号也可以省略。在没被填满的情况默认都补满0\*。所以，

```c
int a[][100] = {
    {0},
    {0},
    {0},};

int b[100][100]={0};
```

十分方便\*。

同时，还可以用循环嵌套。

```c
for(i=0; i<size1 ; i++){
    for (j = 0; j< size2; j++){
        for (k=0; k <size3;k++){
            a[i][j][k]=i+j+k;
        }
    }
}
```

用这样的方式也可以简单地初始化。（注意第二种必须是C99）\*

```c
	int count[5] = {0};
    int a[100] = {[3]=4, [4]=20, [90]=1,2,3,}
```

_\*注：这种情况表示大小的 [ ] 里不可以写int 或const int, 只可以写数字。（原因未知）_

我们可以用sizeof 函数来简单地表示数组的长度

```c
length = sizeof(a)/sizeof(a[0]);
```

## 指针

### 基本操作

int \*p可以定义一个整数地址型（int\* 型）变量 p，同时有int 型变量 \*p

当我们把指针p与变量i联系上时

```c
int i = 6;
int* p = &i;
int**q = &p;
int*** m = &q
```

我们可以用单目运算符 \* 来表示“该地址所指的变量的值”。即 \* 可以将一个地址型变量转化成他所指的数据类型。(-> 表示“\*把左边的数据类型转化成右边的”)

（int\* -> int / double\* -> double / int\*\* -> int\* )。

类似的，单目运算符 & 表示“该变量的地址”，可以将一个变量转化成其对应的地址型变量。

（int -> int\* /  &int\* == int\*\*）

此时，

```c
p == &i, &*&*&*&*p == p, *&*&*&i == i

***m == **q == *p == i

**m == *q == p == &i 
```

但是注意，&不可以连用!!

```c
*m == q == &p != &&i  
```

同时，我们可以：

```c
*p = 20; ==

*&i=20; ==

i = 20;
```

来直接修改“int\* 类型的 p 所指的 int 的值”，即 i 的值。

【为便利，此后的变量类型用斜体表示：i (_int_), p( _int\* _)】

### 常见应用场景

```c
viod swap(int *pa, int *pb){
    int t = *pa;
    *pa = *pb;
    *pb = t;
}
```

或者，如果有一个函数存在可能的错误运算，我们可以让函数返回1,0等来表示他是否出错：

```c
int divide (int a, int b, int *result) {
      //做除法，结果存到result上去
    int ret = 1;
    if(b ==0){
        ret = 0;
    }else{
        *result = a/b;
    }
    return ret;
}

```

### 指针与const

```c
const int *p1 = i
int const *p2 = i
```

在这种情况下前两种表示“你不可以通过\*p = 23”的操作来对i赋值。意味着如果将"const int \*p" 传入一个函数，那么该函数保证不会对i的数值进行修改。

同时，如果向函数传的数据类型的大小要比指针的大小大，通过这种操作可以将较少的字节数传给函数。

```c
int *const p3 = j
```

这表示“p3是一个常数，不可以对p3的值进行修改，他指向j的事实是不可改变的”

### 数组与指针

当我们定义一个数组时

```c
int a[100];
int *p = a;
```

变量a 的就是种数组类型的数据(_a_)，数组类型的数据是一种特殊的指针。a(_int\* _)所指的位置就是a[0]（_int_）的位置。同时p[4]指的就是a[4]

因为数组里的数是紧密排列的，所以我们可以有如下操作：

```c
p = &a[3];

p[1] == a[4]
p[-2] == a[1]

*(p+1) == a[4];
```

注意，这个操作只可以对p(_int\* _)做，不可以对a(_a_) 做，因为你定义一个数组的时候，数组本身已经是一个\*const，a指向的位置是不可改变的，不可以让这个数组再指向别的位置。

```c
const int a[10]={0,1,2,3,4,5,6,7,8,9};
```

意味着数组a里的每一个变量a[i]都是一个const, 在定义之后是不可以再做修改的。所以在定义时必须要做初始化。

```c
sizeof(a) != sizeof(p)
```

前者是数组a = 元素的个数 \* 每个元素的size，但后者就是int\* 型数据的size.

### 指针的计算

当我们对一个指针进行加减运算时，是让地址+sizeof(指针的类型)，即指向下一个数据。所以，这个操作只对连续的数据（数组）有意义。

```c
int a[10];
int *p = &a[2];

p++; p --> a[3]

\\此时 int 的 size = 4， 所以从数字层面来看的话p加了4。 
```

同时我们也可以将指针比大小，通常也只对连续的数据有意义。

如果对指针时间做减法，例如：

```c
int a[10];
int *p = &a[2];
int *q = &a[8];

q-p == 6
```

会得到两个指针之间差几个数据。

### \*p++

\*p++取出了p当时的值，并对p进行了+1。
很多情况，由于\*p++编译比较快，我们可以善用他。例如在遍历数组的时候：

```c
int a[20] = {0,1,2,3,4,5,6,7,8,9,-1};
int *pa = a;

while(*p != -1){
    printf("%d",*p++);
}
```

### NULL

NULL表示0地址，我们可以将一个指针初始化指向NULL，后续如果没让该指针指向其他地址就就对\*p赋值，程序会报错。

### 指针的类型

所有类型的指针大小相等，但是不同类型的指针不可以互相赋值。

````c
char *pc = &c[0];
int *pi = &a[0];```
如果我们这时让 pi = pc，因为*\pi 大小为4字节，\*pc的大小为1字节。
```c
pi = pc
*pi[0] = 0 
    
---> pc[0] == pc[1] == pc[2] == pc[3] == 0;

````

同时，我们可以定义一个指向不知道类型的数据的指针,通常和动态分配内存共用。

```c
void *p 
```

### 函数的指针

函数也是有指针的。函数的名字就可以是他的指针。

```c
void f(int);
int main(void);

此时，f 和 main 就分别是这两个函数的指针

```

我们可以定义一个对应函数指针类型的变量，指向函数。

```c
void f(int);

void (*pf)(int) = f;

此时pf 就是一个 *void(int) 类型的变量
int i = 0;


(*pf)(i);
==
f(i);
```

如果我们想用一个 int 来定义我们接下来使用哪个函数，我们可以使用这种方便的套路。例如：

```c
int plus(int a,int b){
    return a+b; 
}
int minus(int a,int b){
    return a-b;
}
int multiply(int a,int b){
    return a*b;
}
int divide(int a,int b){
    int ret;
    if(b!=0){
        ret = a/b;
    }else{
        ret = -1;
    }
    return ret;
}
int power(int a,int b){
    int i;
    int ret = 1;
    for (i=0;i<b;i++){
        ret *= a;
    }
    return ret;
}

int main(void){
    
    int (*fa[])(int,int) = {plus,minus,multiply,divide,power};
    
    int i;
    int a;
    int b;
    
    scanf("%d %d %d",&i,&a,&b);
    
    if(i>=0 && i < sizeof(fa)/sizeof(fa[0])){
        (*fa[i])(a,b);
    }
    
    
    return 0;
}


```

### 动态分配内存

对于C99以前，我们不可以用 int a[number] 的方式直接定义数组，需要用到malloc 和free函数。

```c
#include <stdlib.h>

int number = 10;
int *a;
a = (int*)malloc(number*sizeof(int));
```

malloc(需要的字节数)，他返回的是void\*，所以需要强制转成int\*后在给a赋值。如果申请内存失败，他就会返回0，也就是NULL。

对于申请来的空间，在用完之后需要用free函数来释放这个空间。但是free的必须是原来申请到的地址，如果地址发生改变，则会出错。同时，如果free一个已经被释放的空间，也会出错。但如果 free(NULL) 是没问题的。

```c
p++;
free(p);  会出错
```

## 字符数组和字符串

我们可以这样定义字符数组，它的性质和普通的数组基本一样。

```c
char word[]={'H','e','l','l','o'};
```

我们有几种方式定义字符串(就是带 \\0 的字符数组)：

```c
char str[]={'H','e','l','l','o','\0'};

char str[]="Hello";

char word[10]= "Jack";
```

第二种方式的话，编译器会自动补一个\\0在最后。所以，一个n个字符的字符串需要n+1个空间。当空间没有被填满的时候，会自动补上''(_char_), 0 (_int_)

双引号里面的内容叫做** 字符串常量**，它存在一个距离普通变量很远的地方，并且是只读的。两个相邻的字符串会自动被连接起来。

同时，我们可以用一个字符指针来指向内容为“Hello”字符串（它的具体地址我们并不知道）：

```c
char *string = "Hello";
char *string1;
srting1 = string;
\\这个操作的意思是我们把“Hello”的地址赋给了string1（char*）
```

当scanf 要把读取到的内容赋给一个不知道长度的字符串，它读取到空格、TAB或回车时，会默认该字符串结束。所以 scanf 只能读取一个单词。一个长度为n的字符数组，最多只应该存放n-1个字符。所以，

```c
char str[10];
scanf("%9s",str);
\\规定了这个输入最多就读到9个就不读了。
```

## 字符串的函数

### putchar getchar 函数

```c
int getchar (viod);
```

类似于 scanf ，从控制台里面每次读入一个字符，返回读到的字符对应的int。当读入的第一个字符为ctrl+Z 时返回-1.

```c
int putchar(int ch);
```

类似于printf()，返回1.

### 如何读取一个字符串？

1.  scanf 

    我们知道，scanf通常只能读取一个单词。我们可以使用%[ ]。它的意义是限定读取[ ]里面的内容。如[ ]里面第一个是'^'，说明“到^后面的字符出现为止”。如：

    ```c
    scanf("%[A-Z]")//只读取大写字母

    char str[1024]
    scanf("%[^\n]"str)//在\n之前都不停止.
    getchar();//进行上一步操作后，需要用getchar把剩下的\n读出来
    ```
2.  getchar
    ```c
    char str[1024];
    int i = 0;
    while((str[i]=getchar())!='\n'){
        i++;
    }
    getchar(); //同样也需要把最后的\n读出来
    ```
3.  gets
    ```c
    char str[1024];
    gets(str);//不需要考虑最后的\n
    ```

### strlen, strcpy, scrcat, scrcmp

首先我们需要包含头文件

```c
#include <string.h>
```

-   int strlen (const char \*a)

```c
char word[] = "people";

strlen(word) == 6 \\字符的个数
sizeof(word) == 7 \\包括\0的字符的个数
```

-   int strcmp (const char\*a, const char\*b)

```c
char a[]="aaaa";
char b[]= "aaba";
strcmp(a,b) ;
    \\一位一位地去对比 a,b 的内容.
        如果有不一样的，则return int a[i]-b[i],否则return 0
```

-   char\* strcpy ( char\* restrict dst, const char\* restrict src)

      把src 所指的内容(包括\\0)赋值给dst，返回dst（地址）.
      restrict 表示 src与dst的地址不可以重复。
      

```c
char* dst = (char*)malloc(strlen(src)+1);
strcpy(dst,src);
```

-   char\* strcat (const char\*a, const char\*b)

      把b 所指的内容接到a 的后面。此时去掉a 最后的\\0，只在最后保留一个\\0。 return a

同时，对于strcpy 和strcat各有一个安全版本strncpy, strncat。最后的参数里输入复制的最大字符数。

-   char\* strcpy (const char\*a, const char\*b, size_t n)
-   char\* strcat (const char\*a, const char\*b, size_t n)

同时，对于strcmp,我们可以用相同的方式规定对比到第几个字符

-   int strcmp (const char\*a, const char\*b, size_t n)

### 字符串搜索函数

-   char \*strchr(const char\* s, int c);
-   char \*strrchr(const char\* s, int c);

      在字符串里搜索字符c，返回寻找到的地址。后者是从右往左找。返回NULL表示没有找到
      

```c
//寻找第二个要找的字符
char s[] = "Hello";
char *p = strchr(s,'l');
p = strchr(p+1,'l');

//打印找到的位置前面的内容
char s[] = "Hello";
char *p = strchr(s,'l');
char temp = *p;
*p = 0;
printf("%s",s);
*p = temp;
```

-   char \*strstr(const char\*s, const char\* t);
-   char \*strcasestr(const char\*s, const char\* t)

这两个函数在字符串里搜索字符串，后者忽视大小写

## 结构类型

### 枚举

```c
enum COLORS {red, yellow, blue, green,NumOfColors};

red == 0, yellow == 1
    
enum month {January = 1, Feburary, March,....}
    //主要用在同时定义许多常量的时候
```

### 结构

#### 声明和初始化结构类型变量

```c
// 通常有这三种声明方式
struct date{
    int month;
    int day;
    int year;
};

struct date today, yesterday;


struct{
    int x;
    int y;
    double value;
} z0,z1,z2;
//没有变量类型的名称，适用于仅需要这几个变量的情况

struct pointofZ{
    int x;
    int y;
    double val;
} z0,z1,z3;
//最常见
```

当然，结构变量的成员仍然可以是一个结构类型的变量

```c
struct point{
    int x;
    int y;
};

struct rect{
    struct point p1;
    struct point p2;
};
```

结构类型变量的初始化和数组有一些类似，如果对一个变量进行了初始化，但仍存在没有初始化的成员，则默认为0

```c
struct date today = {7,1,2021};
struct date thisYear = {.year = 2021};
thisYear.month == 0;
thisYear.day == 0;
```

我们也可以构建由结构类型变量构成的数组

```c
struct date dates[100] = {
    {1,1,1998},
    {30,3,1999},
    {27,11,1998},
};
//由100个date型变量组成的数组，数组的名字（指针）是dates

```

#### 结构基本操作

我们可以用typedef 函数来简化程序

```c
typedef int len;
//给int 起了一个新名字len，用len来做int做的事情

len a = 100;
len sum(len x , double y);
```

同样的事情可以对结构类型变量做

```c
typedef struct ADate{
    int day;
    int month;
    int year;
} date;

date today = {07,1,2021};


```

结构可以这样赋值：

```c
birthday = (struct date){27,11,1998};
birthday1 = birthday;
```

结构变量的名字并不是他的指针，所以必须用 & 来取地址。同时我们有 结构指针->成员 这个运算符来从指针取到成员

```c
struct date *pBirthday = &birthday;
pBirthday -> month = 12;
==
(*pBirthday).month = 12;
==
birthday.month = 12;

so,

scanf("%d", &pBirthday -> month); 
//pBirthday所指向的结构变量（birthday）的成员month的地址
printf("%d", pBirthday -> month);
```

### 联合

联合看起来和结构差不多，他和结构的区别在于，联合中的各个成员只用同一个空间进行储存。

sizeof(union data) == max_i{ sizeof(union data.i) }

```c
union data {
    int i;
    char ch[sizeof(int)];
}
```

如果我们令

```c
data.i = 4D3F(16进制)
```

我们会得到

|     字节     |   0   |   1   |   2   |   3   |
| :--------: | :---: | :---: | :---: | :---: |
|    整数 i    |   3F  |   4D  |   00  |   00  |
| 字符数组 ch\[] | ch[0] | ch[1] | ch[2] | ch[3] |

注意他在内存里是倒序存放的。

## 大程序结构

### 全局变量

定义在main 函数外面的变量是全局变量。他们作用域和存活期都是和整个.c文件一样的。全局变量在内存的位置比本地变量靠前很多。同时，没有初始化的全局变量默认是0，指针默认指向NULL。

函数等内部定义的本地变量的名字可以和全局变量相同。如：

```c
int gALL = 10;
int main (){
    int gALL = 5;
    gALL++;
    gALL == 6
}
gALL == 10
```

在小范围内会忽视全局变量，把本地变量当做一个新的变量。

### 静态本地变量

```c
void f(void){
    static int x = 10;
    x++;
    printf("%d",x);
}

void g(void){
    int y = 10;
    y++;
    printf("%d",y);
}

int main(void){
    f();//x==12
    f();//x==14
    f();//x==16
    g();//y==12
    g();//y==12
    g();//y==12
    return 0;
}
```

这里，y是一个普通的本地变量。每次进入到g函数时y被定义，退出g()时，y的内存就被free掉。

然而x是一个静态本地变量，虽然在f()以外的地方不可以对它进行操作，但在退出f()时他的内存仍然被保存。等到下次进入到f()时它还保留着原来的值。

静态本地变量实际上是一个特殊的全局变量，他在内存里的位置和全局变量是一起的。故，他是更像一个全局生存期，局部作用域的一个全局变量。

翁老师认为：**_尽量不要使用全局变量和静态本地变量。_**

### 宏

我们可以用define来定义一个宏。当一个宏需要换行时，使用 \\ 表示“这个宏还没结束”

```c
#define 宏的名字 宏的内容
#define PI 3.14159
#difine SCAN int i; \
             printf("Hello\n");\
             printf("please give me your value\n");\
             scanf("%d",&i)
```

在编译器编译之前（编译预处理阶段），编译器会机械地将“宏的名字”转化成“宏的内容”。所以在定义宏的时候一定要注意不该加 ; 的地方不能加。例：

```c
int main(){
    
    SCAN;
    printf("%f",i*PI);
    
    return 0;
}

---->
    
int main(){
    
    int i; 
    printf("Hello\n");
    printf("please give me your value\n");
    scnf("%d",&i);
    printf("%f",i*3.14159);
    
    return 0;
}
```

同时，宏还可以带参数。

```c
#define cube(x) ((x)*(x)*(x))


int i;
scanf("%d",&i);

int j = cube(i);
---->
int j = ((i)*(i)*(i));
```

我们在使用这个带参数的宏时，用宏括号里的内容代替定义宏的时候括号里的内容，再将整个宏的名字替换成宏的内容。

注意，宏与函数不同的是，它没有限制数据类型。也容易导致计算的优先级错误。所以在使用带参数的宏时，宏的内容整体要加括号，每一次出现参数时都要给参数加括号。

C语言有一些预定义的宏

```c
    __LINE__ //该行的行号
    __FILE__ //该文件的文件名
    __DATE__ //编译时的日期
    __TIME__ //编译时的时间
    __func__ //宏所处的函数的名字
```

### 大程序

如果我们在Dev c++里新建一个项目，在项目里面放入多个.c文件，那么在编译之前电脑会自动将多个.c文件连起来。很多开发环境必须将.c文件放在项目里才可以形成可执行程序，Dev c++支持单独的.c文件就可以形成可执行程序。

全局变量是可以在多个 .c 文件中共享的。

### 头文件

头文件做的事情实际上是将 .h 文件里的所有文本内容插入的#include那里。

我们通常会在头文件里放入函数以及全局变量的声明，在对应的 .c 文件里放入函数的内容。每一个.c文件都应该有一个对应的.h头文件。

注意全局变量在声明时要加extern 

```c
extern int gAll = 19;
```

### 标准头文件结构

由于函数等不可以重复声明，我们又要使用多个头文件的话，对于在多个头文件中都需要使用的函数（结构等）容易造成重复声明。

为了避免这种情况，我们需要使用标准头文件结构

```c
// 在头文件 linked_list.h中
#ifndef __LINKED_LIST__
#define __LINKED_LIST__

struct linked_list{
    int *array


#endif
```

## 文件

### printf scanf 函数再考

-   printf

```c
%[flags][width][.prec][hIL]type
```

| flags |       意义      |       备注       |
| :---: | :-----------: | :------------: |
|   +   |     正数前写加号    |                |
|   -   |      左对齐      |    通常和宽度一起用    |
|   空格  | 如果没有字符，则放一个空格 |                |
|   0   |     对齐时补0     | 在不影响实际数值大小的情况下 |

| width |    意义   |     备注    |
| :---: | :-----: | :-------: |
|   数字  |  输出的宽度  |           |
|   \*  | 用参数表示宽度 | 参数时后面紧跟着的 |

例：

```c
printf("%-+*d",wid,i);
```

| .prec |    意义   |
| :---: | :-----: |
|  .数字  |    精度   |
|  .\*  | 用参数表示精度 |

精度的意义：

|  对象 |         意义         |
| :-: | :----------------: |
|  整数 |   输出最短位数（不足则用0补）   |
|  小数 |   小数点后保留几位（四舍五入）   |
| 字符串 | 可以输出的最大字符数（超出直接截断） |

修饰类型意味着你要把本来输出的数据当做另一种类型输出

| 修饰类型 |      意义     |
| :--: | :---------: |
|  hh  |  单个字节（char） |
|   h  |    short    |
|   l  |     long    |
|  ll  |  long long  |
|   L  | long double |

|  字符类型 |    意义    |
| :---: | :------: |
| %i,%d |    int   |
|   %u  | 没有符号的int |
|   %o  |    8进制   |
|   %x  |   16进制   |
|   %X  | 16进制字母大写 |
| %g,%G |   float  |
| %f,%F |  float,6 |
| %e,%E |    指数？   |
| &a,&A |  16进制浮点  |
|   %c  |   char   |
|   %s  |  string  |
|   %p  |    指针    |
|   %n  | 读入/写出的个数 |

对于%n

```c
int num;
printf("%d%n",12345,&num);

num 表示 到%n为止输出/写入的字符个数
```

printf的返回值是输出了多少个字符

-   scanf

| flag |      意义     |
| :--: | :---------: |
|  \*  |      跳过     |
|  数字  |    最大字符数    |
|  hh  |     char    |
|   h  |    short    |
|   l  | long,double |
|  ll  |  long long  |
|   L  | long double |

|     字符类型    |        意义       |
| :---------: | :-------------: |
|      %d     |       int       |
|      %i     | 整数，可能为10，8，16进制 |
|      %u     |     没有符号的int    |
|      %o     |       8进制       |
|      %x     |       16进制      |
|      %X     |     16进制字母大写    |
| %a,%e,%f,%g |      float      |
|      %c     |       char      |
|      %s     |      string     |
|      %p     |        指针       |
|    [...]    |      所允许的字符     |

scanf 的返回值是他读入了多少个变量
