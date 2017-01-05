# UIColor >> UIImage Swift 3.0

public func createImageWithColor(_ color: UIColor) -> UIImage? {
    
    //区域大小
    let rect: CGRect = CGRect(x: 0.0, y: 0.0, width: 1.0, height: 1.0)
    
    // 开始绘图
    UIGraphicsBeginImageContext(rect.size)
    
    // 获取绘图上下文
    let context = UIGraphicsGetCurrentContext()
    // 设置填充颜色
    context?.setFillColor(color.cgColor)
    // 使用填充颜色填充区域
    context?.fill(rect)
    
    // 获取绘制的图像
    let image = UIGraphicsGetImageFromCurrentImageContext()
    
    // 结束绘图
    UIGraphicsEndImageContext()
    
    return image
}

使用时直接调用该方法，
let image = createImageWithColor(UIColor.red)
