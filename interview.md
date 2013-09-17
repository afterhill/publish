http://www.cnblogs.com/matt123/archive/2012/12/23/2830290.html

感觉这个还是写的不错的。

1. 作为一名QA，你是怎么理解“质量”这个概念的？

质量是一个产品或者项目表现出来的品质和状态。有多种维度去描述这种品质：

+ 稳定度
+ 健壮性
+ 扩展性
+ 性能
+ 功能性
+ 易用性

对于每一个维度的状况，又有各自独立的评估方式和策略：

+ 单元测试
+ 性能测试
+ 集成测试
+ 功能测试
+ 验收测试
+ GUI测试

对于质量的目标来讲：

+ 质量和成本之间的平衡
+ 质量和项目开发周期之间的平衡
+ 明确可量化的验收指标
+ 清晰可跟踪的milestone
+ 准确的项目健康分析和预测

2. JAVA的垃圾回收机制？内类的几种方式？堆栈的区别？

Java的垃圾回收机制：

+ Java使用自动垃圾回收机制
+ Java使用GC模块实现垃圾回收机制
+ 可以使用System.gc()来调用垃圾回收，但是JVM并不一定保证立即执行
+ finalize()是可以override的方法，gc模块保证在reclaim资源之前，一定执行finalize方法
+ gc对finalizable对象的执行回收是乱序的
+ 可回收对象可以在finalize方法里重生
+ gc里的对象的状态变化为：Reachable & Unfinalized --> F-Reachable & Finalizable --> Reachable & Finalized --> 
Unreachable & Finalized --> Reclaimed

内类的几种方式：

+ 普通内部类，可以访问外部类的对象的实例（包括私有）和方法（包括私有）
+ 匿名内部类

堆栈的区别：

+ Java使用reference type表示对象
+ 所有的java reference 类型的对象都保存在heap中
+ Java 运行时的临时变量，运行时的上下文保存于stack中
+ Java在stack中执行代码

3. 在写自动化框架中，用到了哪些设计模式？

+ 单例模式
+ 工厂模式
+ PageObject模式
+ 组装模式
+ 适配器模式
+ 门面模式
+ 命令模式
+ 策略模式

4. 职业发展规划？

+ 技术track

1. 一些staf、stax的服务命令？

无语。

2. 自动化测试系统如何和CI集成？

+ CI定时从版本库拉取测试用例
+ 基于代码push的触发机制
+ 基于CI的命令行插件去执行测试用例入口代码

3. Domino中邮件路由过程

无语。

算法题：一个字符串，如"This is a test !" ,输出"test a is This",要考虑空间。
