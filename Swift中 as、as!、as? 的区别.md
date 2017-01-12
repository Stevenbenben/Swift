
# 摘自中文api的话：仅当一个值的类型在运行时（runtime）和as模式右边的指定类型一致 - 或者是该类型的子类 - 的情况下，
才会匹配这个值。如果匹配成功，被匹配的值的类型被转换成as模式左边指定的模式。

# as应用条件有两种情况：
1.和"as"右边类型一致。
2.是右边类型的子类（这种情况在Java里叫向上转型）。
```
class Animal {}
class Dog: Animal {}
let a = Animal();
a as Animal    // "a"和右面类型一致，编译成功
let d = Dog();
d as Animal    // "b"是右面类型的子类，编译成功
```

# as!

上例中 第2种情况，是右边类型的子类 如果 碰到as 左边类型是右边类型的父类则会报错！（as不可以用于父类转子类，用java话说，不支持向下转型），
由此可用as！(强转) 
```
class Animal {}
class Dog: Animal {}

let a: Animal = Dog();

a as! Dog   // 编译成功
a as Dog    // 报错
```

# as?

as? 相当于optional类型，如果转换失败返回nil。
```
class Animal {}
class Dog: Animal {}
class Cat: Animal {}

let animal: Animal = Cat();

animal as? Dog      // 取到的是空
animal as? Cat      // 取到Cat
animal as! Dog      // 报错
```


