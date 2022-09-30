# 类型别名typedef

> 有using，#define，typedef三种形式，但一般使用typedef来定义（为了程序的可兼容性考虑）

### typedef定义多种类型别名

初级

```c++
typedef int type;//算数类型
typedef int* type;//指针
typedef struct{char c;} type;//结构体
typedef struct test{
    char c;
}type;//给test结构体定义一个别名type
typedef int type[5];//数组
typedef char* type[5];//指针数组
typedef char* (type[5]);//还是指针数组，[]运算符优先级最高
```

定义函数(**仅仅对声明有用**)

```c++
typedef int (FUNC)(int, int);
FUNC test{
    //process
}
FUNC add;
int add(int a,int b){
//process
}
```

复杂指针的定义

> 复杂指针阅读按照右左规则：
>
> 从变量名看起，先往右，再往左，碰到圆括号就调转阅读的方向；括号内分析完就跳出括号，还是先右后左的顺序。如此循环，直到分析完整个定义。
>
> int (*p[10]) (int) -- p，p是一个数组，p是一个指针数组，p是一个函数指针（参数为int），p的返回值为int
>
> float (* (*fp2) (int, int, float)) (int)  -- fp2是一个指针，fp2是一个函数指针，fp2指向的函数的返回值还是指针，返回的指针指向float(int)这个函数
>
> int (* (*fp4()) [10]) ()--fp4是一个函数，fp4返回指针(p1)，p1指向一个指针（p2）数组，p2指向一个int函数

```c++
typedef int(*type)[10];//指向十个int类型数组的指针
typedef int(*type)[10][10];//多维数组指针
typedef void(*type)(int,int);//函数指针
typedef double (* (* (*type) ()) [10]) ();//
```

### typedef的作用域

typedef定义在文件中，那么就是文件头到文件尾。

typedef定义在函数中，就是函数头到函数尾。

typedef定义在类中，就是与类的作用域相同。

定义在头文件中，就是引用该头文件的文件。

注：**与函数和全局变量不同，函数和全局变量在一整个项目中都不能重名，但是typedef可以，只要两者作用域不交叉即可**

### 类内的类型别名

定义在public中的类型别名，可以通过作用域运算符在类外面使用

```c++
class X{
public:
typedef double d;
};
X::d test();
```

定义在private中的类型别名，不能通过作用域运算符在类外面使用，只能在类内使用

```c++
class X{
private:
typedef double d;}
X::d test();//error
```

在类中，typedef不能覆盖

```c++
typedef double money;
class Account{
    private:
    typedef double Money;
    Money bal;//error,二义性错误。
};
```

