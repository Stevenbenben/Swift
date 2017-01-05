# 预处理指令

Swift编译器不包含预处理器。取而代之的是，它充分利用了编译时属性，生成配置和语言特性来完成相同的功能。
因此，Swift没有引进预处理指令。

# 简单宏

在C和Objective-C，您通常使用的#define指令定义的一个基本常数，在Swift，您可以使用全局常量来代替。
例如：一个全局定义#define FADE_ANIMATION_DURATION 0.35，在Swift可以使用let FADE_ANIMATION_DURATION = 0.35来更好的表述。
由于简单的用于定义常量的宏会被直接被映射成Swift全局量，Swift编译器会自动引进在C或Objective-C源文件中定义的简单宏。

# 复杂宏

在C和Objective-C中使用的复杂宏在Swift中并没有副本。复杂宏是那些不用来定义常量的宏，包含带括号的函数式宏。
您在C和Objective-C使用复杂的宏以避免类型检查的限制，或避免重新键入大量的样板代码。然而，宏也会产生Bug和重构的困难。
在Swift中你可以使用函数和泛型来达到同样的效果，无需任何的妥协。因此，在C和Objective-C源文件中定义的复杂宏在Swift是不能使用的。

# 编译配置

Swift代码和C、Objective-C代码被有条件地，以不同方式编辑。SWIFT代码可以根据生成配置的评价可以有条件地编译。
生成配置包括true和false字面值、命令行标志以及下表中的平台测试函数。您可以使用-D <＃Flag＃>指定命令行标志。

# 需求解决

建立一个类，将过去需要建立的那些简单的宏，设为全局变量，例如这样

```
import UIKit

public let MAIN_SCREEN_WIDTH: CGFloat = UIScreen.main.bounds.size.width
public let MAIN_SCREEN_HEIGHT: CGFloat =  UIScreen.main.bounds.size.height

class AppDefines: NSObject {

}
```
