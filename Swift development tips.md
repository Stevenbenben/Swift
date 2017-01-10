# 几个加速Swift开发的小tip

主要内容有：

- private(set)语法
- 分号的使用
- 利用String类型初始化方法简化UITableViewCell的reuseIdentifier
- 简洁的声明多个变量
- 压轴推荐：Xcode断点调试小技巧

## private(set)
出于代码安全性的考虑，如果一个类的属性不会被其他类使用，那么可以把它声明为private。更进一步我们可以使用private(set)关键字告诉编译器，
这个类对外可读但是不可写，比如：
```
// In other swift file
struct Person {
    private(set) var name = "Unknown"
}

// In main.swift
// 可以获取name属性的值
print(person.name)

// 报错，不能在PrivateSet.swift文件外对name属性赋值
//person.name = "newName"
```
这个属性只能在文件内部被读写，即使是在结构体的定义外也可以。但是在别的文件中就不能对其赋值了。

需要强调的一点是，只有private(set)关键字，并没有private(get)关键字。


## 利用好分号

分号在Swift中几乎退出了历史舞台，但在某些情况下使用分号也是不错的选择。

假设在函数的开头有一个guard判断，如果判断不成立则退出函数，并输出一些调试信息，过去的版本可以这样写：
```
func doSomething() {
    let error: AnyObject? = nil
    guard error == nil
        else {
            print("Error information")
            return
        }
}
```
如果使用分号，可以简化代码，它把代码压缩在一行语句中，简洁又不失可读性：
```func doSomething() {
    let error: AnyObject? = nil
    guard error == nil else { print("Error information"); return }
}
```

## reuseIdentifier
给cell一个reuseIdentifier是一件挺麻烦的事情，首先不能瞎起名字，比如let reuseIdentifier = "reuse"。一旦同一个UITableView中有两种
或更多cell，事情就比较麻烦了。

这就要求我们为reuseIdentifier赋值是要考虑到字符串的具体含义，比如代码可能是这样的：
```
let reuseIdentifier = "TableViewCommentCellIndentifer"
```

作为一个喜欢偷懒的人，为了节省起名字以及输入这些字符串的时间，我们完全可以这样写
```
let reuseIdentifier = String(TableViewCell)
```
这里的TableViewCell是自定义的UITableViewCell的子类，把它传入字符串的构造函数中得到的结果是"TableViewCell"，一切显得那么和谐简介。

## 简洁声明多个变量

对于一些相互有关联的变量，相比于在每行中声明一个，还有一种更简洁美观的方式：
```
var (top, left, width, height) = (0.0, 0.0, 100.0, 50.0)
//rect.width = width
```

## Xcode断点调试小技巧
具体参考[bestswifter](http://www.jianshu.com/p/5ebd5e8ecf60)





