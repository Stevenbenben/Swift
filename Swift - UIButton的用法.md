# 1，按钮的创建
(1)按钮有下面四种类型：
	UIButtonType.system：前面不带图标，默认文字颜色为蓝色，有触摸时的高亮效果
	UIButtonType.custom：定制按钮，前面不带图标，默认文字颜色为白色，无触摸时的高亮效果
	UIButtonType.contactAdd：前面带“+”图标按钮，默认文字颜色为蓝色，有触摸时的高亮效果
	UIButtonType.detailDisclosure：前面带“!”图标按钮，默认文字颜色为蓝色，有触摸时的高亮效果
	UIButtonType.infoDark：为感叹号“!”圆形按钮
	UIButtonType.infoLight：为感叹号“!”圆形按钮
  
```
  //创建一个ContactAdd类型的按钮
let button:UIButton = UIButton(type:.contactAdd)
//设置按钮位置和大小
button.frame = CGRect(x:10, y:150, width:100, height:30)
//设置按钮文字
button.setTitle("按钮", for:.normal)
self.view.addSubview(button)
```

(2)对于Custom定制类型按钮，代码可简化为： 
```
let button = UIButton(frame:CGRect(x:10, y:150, width:100, height:30))
```

# 2，按钮的文字设置
```
button.setTitle("普通状态", for:.normal) //普通状态下的文字
button.setTitle("触摸状态", for:.highlighted) //触摸状态下的文字
button.setTitle("禁用状态", for:.disabled) //禁用状态下的文字
```

# 3，按钮文字颜色的设置 
```
button.setTitleColor(UIColor.black, for: .normal) //普通状态下文字的颜色
button.setTitleColor(UIColor.green, for: .highlighted) //触摸状态下文字的颜色
button.setTitleColor(UIColor.gray, for: .disabled) //禁用状态下文字的颜色
```

# 4，按钮文字阴影颜色的设置 
```
button.setTitleShadowColor(UIColor.green, for:.normal) //普通状态下文字阴影的颜色
button.setTitleShadowColor(UIColor.yellow, for:.highlighted) //普通状态下文字阴影的颜色
button.setTitleShadowColor(UIColor.gray, for:.disabled) //普通状态下文字阴影的颜色
```

# 5，按钮文字的字体和大小设置 
```
button.titleLabel?.font = UIFont.systemFont(ofSize: 11)
```

# 6，按钮背景颜色设置 
```
button.backgroundColor = UIColor.black
```

# 7，按钮文字图标的设置  
（1）默认情况下按钮会被渲染成单一颜色 
```
button.setImage(UIImage(named:"icon1"),forState:.Normal)  //设置图标
button.adjustsImageWhenHighlighted=false //使触摸模式下按钮也不会变暗（半透明）
button.adjustsImageWhenDisabled=false //使禁用模式下按钮也不会变暗（半透明）
```

（2）也可以设置成保留图标原来的颜色
```
let iconImage = UIImage(named:"icon2")?.withRenderingMode(.alwaysOriginal)
button.setImage(iconImage, for:.normal)  //设置图标
button.adjustsImageWhenHighlighted = false //使触摸模式下按钮也不会变暗（半透明）
button.adjustsImageWhenDisabled = false //使禁用模式下按钮也不会变暗（半透明）
```

# 8，设置按钮背景图片
```
button.setBackgroundImage(UIImage(named:"bg1"), for:.normal)
```

# 9，按钮触摸点击事件响应 
```
//不传递触摸对象（即点击的按钮）
button.addTarget(self, action:#selector(tapped), for:.touchUpInside)
func tapped(){
     print("tapped")
}
 
//传递触摸对象（即点击的按钮），需要在定义action参数时，方法名称后面带上冒号
button.addTarget(self, action:#selector(tapped(_:)), for:.touchUpInside)
 
func tapped(_ button:UIButton){
     print(button.title(for: .normal))
}
```

常用的触摸事件类型：
touchDown：单点触摸按下事件，点触屏幕
touchDownRepeat：多点触摸按下事件，点触计数大于1，按下第2、3或第4根手指的时候
touchDragInside：触摸在控件内拖动时
touchDragOutside：触摸在控件外拖动时
touchDragEnter：触摸从控件之外拖动到内部时
touchDragExit：触摸从控件内部拖动到外部时
touchUpInside：在控件之内触摸并抬起事件
touchUpOutside：在控件之外触摸抬起事件
touchCancel：触摸取消事件，即一次触摸因为放上太多手指而被取消，或者电话打断

http://www.hangge.com/blog/cache/detail_529.html
