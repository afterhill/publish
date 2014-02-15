发信人: rensheng (rensheng), 信区: JobHunting       
标  题: G家onsite面经         
发信站: BBS 未名空间站 (Fri Feb 14 20:03:08 2014, 美东)               

出来混了6年，想换换环境。可能是因为local，google没有给我电面直接onsite了。自己感觉onsite表现还不错，但是还是被拒。我就简单把题目分享给大家吧。面的Java position。所以写的都是java code。

###1. 白人。

a. 设计自己的一个Iterator class。 constructor输入的是List<Iterator>. 实现一个method: Object getNext(); 每次得出的结果如下。

加入输入是

  Iterator1: a, b, c, d, e
  Iterator2: f, g, h, i, j

getNext() 出来的顺序是 a, f, b, g, c, h, d, i, e, j

写完代码后直接问我time complexity 然后就move on下一个题了。。。也没有跟我discuss还是walk through一下code。

b. 问我在什么情况下选择n^2的复杂度而不是nlogn. Open ended question。

c. f(string a, string op, string b)， 要我写出各种testing cases。

###2. 白人
a. implement thread-safe queue class

b. all the combination of letters of phone number (leetcode 原题)

写完代码， 一样也是问了下time complexity就move on了。。。

###3. 貌似中国人

a. 讲了一会自己做的产品

b. 给9个9 还有 +,-,*, /, ()。 让返回无法表示的最小的正数。

比如 如果 1 无论怎么用这些运算符组合9个9，那就返回1.

开始没有头绪，给了提示问如果只给出一个9怎么办，如果只给2个9怎么办。就想到了recursive，终止条件是 当9的数量为1的时候，查的数是9就是true，其余都是false。

两个9的时候，查的数是1(9/9),18(9+9),81(9*9)就返回true。

```
else if (isValid(target/9, num-1))
else if (isValid(target*9, num-1))
else if (isValid(target+9, num-1))
else if (isValid(target-9, num-1))
else if (isValid(9-target, num-1))
else if (isValid(9/target, num-1))
return false;
```

虽然代码没有最后写完。面试官认可了这个算法

###4.白人，最简单的题

```
interface TreeNode{
  int getNumChild();
  TreeNode getChild(int index);
}
```

int numberofNodes(TreeNode) 实现这个method，得出一个tree里node的数量。一个node可以有任意数量的子节点。每个节点的子节点按顺序从左到右的index都是0,1,2,...

我就用bfs， queue几行就实现了。

然后面试官各种各种的演变。比如边变成有向边，一个节点会有多个父节点。其实就是变成了graph。用一个set保留所有第一次访问过的节点就行了。

然后继续考虑在多线程的情况下会出现什么情况。我说不影响。

他继续play around. 这个TreeNode 增加了 Boolean visited。 看看在现有的代码下，多线程会出现什么错误，不要求改代码就是讨论玩玩。

###5. ABC

已经很累了。。。

string getDecimal(int a, int b)  a/b 输出小数的表示。比如 2/5=0.4 要输出 0.4. 如果有无线循环小数则把重复的数放在（）里。比如 1/6 应该返回 0.1(6)
