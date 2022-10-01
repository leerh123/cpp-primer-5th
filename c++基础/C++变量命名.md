# C++变量命名

## 一.类型命名

> 包括类，结构体，枚举，template，using，typedef等

大写字母开始，每个单词的首字母均大写，不包含下划线

```c++
// 类和结构体
class UrlTable { ...
class UrlTableTester { ...
struct UrlTableProperties { ...
    
// 类型定义
typedef hash_map<UrlTableProperties *, string> PropertiesMap;

// using 别名
using PropertiesMap = hash_map<UrlTableProperties *, string>;


```



## 二.变量和常量命名

普通变量首字母小写，中间用下划线连接。

成员变量以“_”结尾。

函数形参以“_”开头

全局变量以"g_"开头

静态变量以"s_"开头

常量以 “k” 开头, 大小写混合. 例如: **const** int kDaysInAWeek = 7;

## 三.宏命名

全大写 + 下划线， 例如：

```c++
#define ROUND(x) ...
#define PI_ROUNDED 3.0
```

## 四.函数命名

常规函数命名方法同类：`MyExcitingFunction()`,`MyExcitingMethod()`

get、set等函数命名：`set_age()` ， get_age()

## 五.命名空间命名

全小写 + 下划线

例如：`websearch::index`,`websearch::index_util`