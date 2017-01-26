# 一、简介
如今，函数响应式编程成为越来越受Swift开发商欢迎的编程方法。原因很简单，它能使复杂的异步代码容易地编写和理解。
在这篇文章中，我要比较GitHub上提供的两个最流行的函数响应式编程库——RxSwift与ReactiveCocoa。
首先，我们将简要回顾什么是函数响应式编程，然后详细比较这两个框架。本文结束时，你会决定哪一个框架更适合你！

ReactiveCocoa GitHub链接 [ReactiveCocoa](https://github.com/ReactiveCocoa/ReactiveCocoa)

ReSwift GitHub链接 [ReSwift](https://github.com/ReSwift/ReSwift)


# 二、什么是函数响应式编程（FRP）
甚至在苹果公司宣布Swift语言之前，函数响应式编程在近几年已人气剧增，从而与面向对象编程形成鲜明对比。从Haskell到Javascript，
你都能够发现其中包含着受函数响应式编程启发而存在的支持。这是为什么？函数响应式编程提供了什么特别的支持？也许最重要的是，你该
怎样在Swift编程中使用这一技术？
FRP是一种由Conal Elliott创建的编程范式。他定义了有关FRP的非常具体的语义（请参考https://stackoverflow.com/questions/1028250/what-is-functional-reactive-programming）。为了实现更简洁的定义，FRP组合了另外两个功能概念：
l  响应式编程（Reactive Programming）：侧重于异步数据流，你可以监听这种数据流并迅速做出相应的反应。要了解与之相关的更多信息，请查阅https://gist.github.com/staltz/868e7e9bc2a7b8c1f754。
l  函数式编程（Functional Programming）：强调通过数学语言风格的函数、不变性和表现力来实现计算，并最小化变量和状态的使用。请参阅百度百科（http://baike.baidu.com/link?url=oTiEJsaX5ibGvK3R-BK6J55dGOXf3-Zzn5e1uBpvWDx4AjCV8ykQtRWz3RmuUefjD6IzL_QZcyedkvMB8sEyhK）进一步了解这种编程范式。
