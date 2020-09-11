# RTTI
RTII是运行阶段的类型识别（RUN TYPE IDENTIFICATION）的简称。

## RTTI的用途
派生对象可能包含不是继承而来的方法，在这种情况下，只有某些类型的对象可以使用该方法；
跟踪生成的对象的类型。

## RTTI的工作原理
- 如果可能的话，dynamic_cast运算符将使用一个指向基类的指针来生成一个指向派生类的指针，否则该运算符返回0-空指针；
- typeid运算符返回一个指出对象的类型的值；
- type_info结构储存了有关特定类型的信息；
只能将RTTI用于包含虚函数的类层次结构，原因在于只有对于这种类层次结构，才应该将派生对象的地址赋给基类指针；

### dynamic_cast运算符
dynamic_cast运算符是最常用的RTTI组件，它不能回答“指针指向的是哪个类型的对象”，但能够回答“是否可以安全地将对象的地址赋给特定类型的指针”。
```c++
class Grand{//has virtual method};
class Superb:public Grand{...};
class Magnificent:public Superb{...};

w570778933
timj3ly@gmail.com
101180010793

//指针
Grand* pg = new Grand;
Grand* ps = new Superb;
Grand* pm = new Magnificent;

//类型转换
Magnificent* p1 = (Magnificent* ) pm;
Magnificent* p2 = (Magnificent* ) pg;
Superb* p3 = (Magnificent* ) pm;

```

