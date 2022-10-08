# struct 

> struct除了默认访问权限为public之外，和class没有明显区别

# Union

>1. 同一内存在每一瞬时只能保存一个成员。***\*所有成员的首地址都是一样的\****。为了使得所有成员能够共享一段内存，因此***\*该空间必须足够容纳这些成员中最宽的成员\****。
>2. 起作用的成员是**最后一次赋值的成员**

```c++
共用体的赋值和使用问题
#include <stdio.h>
#include <string.h>
 
union Data
{
	int i;
	float f;
	char str[20];
};
//共用体占用的内存是共用体中最大的成员所占内存，因为这样才能足够存储共用体中最大的成员。
//例如，在上面的实例中，Data 将占用 20 个字节的内存空间，因为在各个成员中，字符串所占用的空间是最大的。
 
int main()
{
	union Data data;//使用前要加一个union
 
	data.i = 10;
	data.f = 220.5;
	strcpy(data.str, "C Programming");
 
	printf("data.i : %d\n", data.i);
	printf("data.f : %f\n", data.f);
	printf("data.str : %s\n", data.str);
 
	return 0;
}
```

在上述代码中，只有str可以打印出正常的值。i和f都是乱码。

**只能对一个元素赋值，这是union的目的**

# enum

> 是一种整型，省去了一个一个define的繁琐

枚举是一种高级数据类型

一般形式为：enum　枚举名　{枚举元素1,枚举元素2,……};

例如：enum Season {spring, summer, autumn, winter};

### 枚举的定义

#### 1.先定义枚举类型，再定义枚举变量

```c++
enum Season { spring, summer, autumn, winter };
enum Season s;
```

#### 2.定义枚举类型的同时定义枚举变量

```c++
enum Season { spring, summer, autumn, winter } s;
```

#### 3.省略枚举名称，直接定义枚举变量

```c++
enum { spring, summer, autumn, winter } s;
```



### 相关语法

#### 1、C语言编译器会将枚举元素(spring、summer等)作为整型常量处理，称为枚举常量。

#### 2、枚举元素的值取决于定义时各枚举元素排列的先后顺序。默认情况下，第一个枚举元素的值为0，第二个为1，依次顺序加1。

```c++
enum Season {spring, summer, autumn, winter};
```





也就是说spring的值为0，summer的值为1，autumn的值为2，winter的值为3

 

#### 3、也可以在定义枚举类型时改变枚举元素的值

```c++
enum season {spring, summer=3, autumn, winter};
```

没有指定值的枚举元素，**其值为前一元素加1**。也就说spring的值为0，summer的值为3，autumn的值为4，winter的值为5。

 

## 操作枚举变量

1.赋值：可以给枚举变量赋枚举常量或者整型值

```c++
enum Season {spring, summer, autumn, winter} s;
s = spring; // 等价于 s = 0;

s = 3; // 等价于 s = winter;
```



2.遍历枚举元素

```c++
enum Season {spring, summer, autumn, winter} s;

// 遍历枚举元素
for (s = spring; s <= winter; s++) {
    printf("枚举元素：%d \n", s);
}
输出：
枚举元素：0
枚举元素：1
枚举元素：2
枚举元素：3
```

**注：enum和union的实例化格式为enum/union  <类型名>  <变量名>，前面的enum/union不能省略!**

