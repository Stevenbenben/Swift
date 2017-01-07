# 1，结构体struct和枚举enum的静态属性，静态方法使用static关键字 

```
struct Account { 
    var amount : Double = 0.0                 //账户金额 
    var owner : String = ""                   //账户名 
 
    static var interestRate : Double = 0.668  //利率
 
    static func interestBy(amount : Double) -> Double {
        return interestRate * amount 
    }
}

```

# 2，类class的类型属性，类型方法使用class关键字 

```
class Account {
    var amount : Double = 0.0               // 账户金额 
    var owner : String = ""                 // 账户名 
  
    class var staticProp : Double {
        return 0.668 
    } 
 
    class func interestBy(amount : Double) -> Double {
        return 0.8886 * amount 
    }
} 
   
//访问静态属性 
print(Account.staticProp)
```

[原文出处](http://www.hangge.com/blog/cache/detail_520.html)
