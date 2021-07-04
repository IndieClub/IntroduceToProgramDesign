# 引言

ECS:

-   最大程度解耦
- 编写难度大,培训成本大
-   更新与数据有条不紊

CS:

-   较大程度解耦

-   更新一般
- 刚刚好

OOP:

-   十分简单,能够很快的进行游戏原型的制作

SMAN:

-   System 系统

-   Mechanism 机制

-   Assets 资产

-   Network 网络

## 计划

现在面向对象的编程,已经普及.

面向数据的编程,在缺乏完备的工作流的情况下,不适合团队工作.

因此,面向数据的编程非常适合我们未来的发展.

毕竟谁不喜欢3A呢?

而且Unity已经帮我们把轮子都造好了qwq.

以后咱们可以搞一个属于China的纯ECS引擎

我们将处于,并长期处于使用UE4的CS模式.

-   UE4是最好的引擎

-   将机制完全解耦,是针对游戏制作非常完美的做法.

-   

## ECS

Entity: Componet的合集

Component: 数据的储存

System: 通过便利不同Component的组合,进行相关的逻辑处理

优点:

-   功能,完全解耦.

-   性能高

-   在"文案"的辅助下,非常容易理解

-   你需要了解整个项目,才能够开始研发,极大保护了代码,以及程序猿对项目的把控

缺点:

-   入门高门槛

-   你需要了解整个项目,才能够开始研发,不方便新人进入

-   在缺少"文案"的辅助下,如同天书

**延迟处理**

其延迟处理技巧,相比于OOP是优势中的优势

在ECS中

System之间禁止调用，对象间的交互需要用到延迟处理的技巧。

比如A攻击了B，我们需要A攻击和相关数据记录下来,也就是添加组件.

等专门处理受击的系统处理到B的时候再计算对B造成的伤害。

如果B对A有反弹伤害, 我们需要等到下一次 更新进行处理.

在传统模式中

A攻击了B,直接调用B中受到攻击有关的方法,
这样子做法虽然简单,好用,但是当两个人都持有反伤的时候, A又对B有反弹伤害,B又对A有,
那么你就会卡在"互相反弹"的黑洞里去

ECS能够平滑的处理整个游戏的逻辑.

**理解**

ECS模式中,

Component 让你把机制彻底解耦,让你能够清楚的了解,这个东西是由什么部分组成的

System: 则让你知道事情的发展顺序, 清楚了解到底层的运行是什么样的

## 机制,组件,框架

游戏中的任何一共概念,都可以使用这个东西进行划分

解耦: 根据项目的难度,进行合适的解耦,是区分系统策划职级的重要条件.
这个东西非常的抽象

机制: 游戏的基本元素

组件: 将机制进行解耦的划分.

解耦,就是把一件事彻底分类. 比如说一个箱子, 能够被玩家打开, 打开后会掉落各种东西.

-   箱子的模型

-   打开掉落的物品的生成

-   玩家打开的操作

或者说, 玩家的生命值, 会在下雪的时候减少

-   玩家的生命值

-   下雪减少生命值

-   这个例子也可以直接弄一个 玩家生命值组件把下雪减少生命值储存进玩家.
    但是,如果环境类的东西比较多, 尽可能进行细分比较好.

系统: 不同机制之间的数据交换, 比如说伤害系统.