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

4. 算法题：一个字符串，如"This is a test !" ,输出"test a is This",要考虑空间。

```
    public static void main(String[] args) {
        String s = "This is a test!";
        String splited[] = s.split("\\s+");
        int len = splited.length;
        String temp = null;
        for(int i = 0; i < len / 2; i++) {
            temp = splited[i];
            splited[i] = splited[len - i - 1];
            splited[len - i - 1] = temp;
        }
        System.out.println(Arrays.toString(splited));
    }
```

5. 设计模式：对单例模式的理解，有几种实现方式。

+ double check + volatile
+ static method and field
+ enum

6. Python: 字符串查找

+ `xx in xxx`
+ s.find(...)
+ `xx.__contains__()`
+ s.rfind(...)
+ s.index(...)

7. 口语题：你安排了一次团队活动，现在去给老板汇报，讲清楚：时间、地点、交通、具体活动安排。
第二轮的时候，面试官会问，如果有一名RD手头有活，不愿意参加，你怎么说服他参加。

无语。

8. 在自动化实施过程中成本最大的一部分是什么

测试用例开发。

9. 在实现自动化过程遇到的最大困难，是如何解决的？

自动化开发的流程滞后，代码不规范，导致早起自动化对象维护困难。

10. Java: HashMap与HashTable的区别

+ HashMap是线程不安全的，允许key和value里有null值
+ HashMap基于Iterator遍历
+ HashMap是fast-fail的，如果在遍历的时候，底层的数据发生了结构性的改变
+ HashTable是legacy Java的实现
+ HashTable是线程安全的
+ HashTable不是fast-fail的
+ HashTable的遍历基于enumerator对象，不是fast-fail
+ HashTable对Dictionary借口的实现，是obsolete

11. Java: 对抽象类与接口的理解

+ 接口可以多继承
+ 抽象类只能单继承
+ 接口不可以实现方法
+ 抽象类可以实现方法
+ 抽象类用来生成样本代码boilerplate

12. 设计模式：如何实现线程安全的单例模式

同上。

13. 设计模式：监听者模式

？ 待补充

14. 算法题：判断一个链表是否有环

Flyoid Tortorise and Hare Algorithm

15. 算法题：字符串左旋

？

16. 算法题：二叉树中，两个节点间的最大路径。

tree diameter

17. 自动化框架的实现，为什么这么做？

+ 扩展性
+ 适用性
+ 健壮性

18. 自动化过程中遇到的难点，困难？

+ 不可识别对象
+ 代码格式不同意，流程滞后
+ 框架的弹性不强

19. 面向对象的特性，简单阐述这些特性带来的优势

+ 继承
+ 多态
+ 分层
+ 抽象
+ hook

20. 接口与抽象类的区别

已有。

21. 异常类处理机制

+ try catch
+ throw
+ 分层的异常处理机制
+ 只处理需要处理的，其他抛出去

22. 反射机制，在实际写代码中应用

+ hook
+ proxy
+ annotation

23. final,finally,finalize的区别

+ final必须在初始化完成之后必须有值
+ 不能override，一旦赋值不能更改
+ 线程安全
+ finally，try catch模块中一定被执行
+ finalize，gc中一定会被执行

24. 有没有用过spring框架

呵呵

25. 测试用例设计题：就linux下的CP命令设计测试用例。

+ argument type
+ argument length
+ return type
+ return length
+ multiple argument combination
+ integration with other command

26. 如果让你设计一些log监控系统，你会从哪些方面考虑？

+ 监控粒度
+ 监控界面
+ 监控项的可配置性
+ 扩展性
+ 健壮度
+ 性能
+ 存储方式
+ 分布式
+ 架构




