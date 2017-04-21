# Block方法声明

```
- (void)testBlock:(NSString *)value completeBlock:(void(^)(BOOL isComplete))completeBlock {

    NSLog(@"%@", value);
    completeBlock(YES);
}
```

# Block方法调用

```
[self testBlock:@"testBlock" completeBlock:^(BOOL isComplete) {
  if (isComplete) {
    NSLog(@"isComplete is YES:%d", isComplete);
  } else {
    NSLog(@"isComplete is NO:%d", isComplete);
  }
}];
```

# Block变量声明与实现

## 声明

```
@property (nonatomic,copy) void(^testBlock)(NSString *value, void (^completeBlock)(BOOL isComplete));
```

## 实现
```
if (self.testBlock) {

  self.testBlock(@"testBlock", ^(BOOL isComplete) {
            
    if (isComplete) {
      NSLog(@"isComplete is YES:%d", isComplete);
    } else {
      NSLog(@"isComplete is NO:%d", isComplete);
    }      
    
  });
}
```


# Block变量调用

```
self.testBlock = ^(NSString *value, void (^completeBlock)(BOOL isComplete)) {
        
  NSLog(@"%@", value);
  completeBlock(YES);
        
};
```


# 方法与变量写法区别：

completeBlock:(void(^)(BOOL isComplete))completeBlock

void (^completeBlock)(BOOL isComplete)


testtest

