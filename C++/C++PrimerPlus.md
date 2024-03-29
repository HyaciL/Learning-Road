# C++ Primer Plus


## 第七章 函数

### 7.10 函数指针



## 第八章 函数探幽
### 8.1 内联函数

### 8.2 引用变量
**引用变量**是一种伪装指针,主要用作处理结构和类对象的函数的参数.
- 基类引用可以指向派生类对象

### 8.3 默认参数
只能从右到左提供*默认参数*
### 8.4 函数重载
函数特征标:函数重载的关键--***参数列表***
没有对应的函数定义时,会进行强制转换;
- 有多个可转换函数对象时,报错
- 不能共存的函数特征标
  - 类型引用和类型本身视为同一个
  - 不区分const和非const

### 8.5 函数模板
#### 显式具体化
#### 隐式实例化和显式实例化

#### 编译器选择函数
重载解析：
1. 创建候选函数列表：名称相同的函数和模板；
2. 创建可行函数列表：参数数目正确的函数（包含隐式转换）
   >int型不能隐式转换为double* 或赋给double&;
3. 选择：
   1. 完全匹配和最佳匹配:如果由多个完全匹配,可能会报Ambiguous(二义性错误)
    > 特例:指向非const数据的指针和引用,优先与非const指针和引用匹配;
    > 另一特例就是模板等
    - 模板匹配时根据"most specialized",值编译器推断使用那种类型执行的转换最少
    - 用于找出最具体模板的规则称为函数模板的**部分排序规则**,和显式示例一样,C++98新增;

#### 模板函数的发展
##### 不确定类型问题
如当存在类型提升时，可能不知道应该使用什么类型；
~~~c++
template<class T1,class T2>
void ft(T1 x,T2 y)
{
   ...
   ?type> xpy = x+y;
   ...
}
~~~
C++11新增关键字： **decltype**
~~~c++
int x;
decltype(x)y; //make y the same type as x;
//应用如下
decltype(x+y)xpy;
xpy = x+y;
~~~
decltype中，为确定类型，编译器必须遍历一个**核对表**；
另一种无法解决的情况，函数返回值不明确时，要在声明参数后使用decltype（），即使用**后置返回类型**；
~~~c++
auto h(int x,double y) ->decltype(x+y)
{
   ...
}
~~~
此时decltype(x+y)在作用域内;


## 第九章 内存模型和名称空间
