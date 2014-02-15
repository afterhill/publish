发信人: yycosammx (squarY), 信区: JobHunting      
标  题: L家Onsite面经                 
关键字: Linkedin                        
发信站: BBS 未名空间站 (Sat Feb 15 02:18:24 2014, 美东)                             

6轮skype视频面(人在国内)，没有要签NDA之类的，分享下，攒RP

###1. 阿三经理

80年代IIT毕业，口音没问题       
+ a. 问项目经验
+ b. 分布式相关问题，没深入细节，包括2pc, paxos, zookeeper的实现等

###2. 波兰小伙

有点害羞，但人非常好。                 
+ a. message{msgId,byte[]}。大量message持续的input，要支持Message[] getAll(msgId)，问怎么存储message。

###3. 阿根廷帅哥

专做搜索的，长的好像诺维斯基。。。    
问题：如何设计分布式倒排索引，如何进行query。

###4. 阿三

小印，口音重，发了篇SIGMOD，不过第一作者是国人:)

+ a. 假设有函数int[] getConnection(memberID)，结果是有序的，要求实现：
  + isFirstDegree(member1,member2)
  + isSecondDegree(member1,member2)
  + isThirdDegree(member1,member2)

就是判断一度，二度，三度好友关系，是系统设计题，伪代码即可。

follow up：分布式下怎么做

+ b. tinyurl

follow up:问如何scala-out

###5. 埃塞俄比亚小伙

悲剧的一轮，小伙人很好，但英语比阿三还难懂，有史以表现最差的一次。

+ a. 给一个矩阵，followMatrix[i][j]==true，表示j影响了i。求influencer，即影响所有人，且不被任何人影响
+ b. 三角形问题，输入一些线段的长度，找出能形成三角形的三条线段

###6. 老美

表现最好的一轮，有相似的项目经验，聊的比较投机

+ a. max points on a line
+ b. 给int[] a,求int[] result。 其中result[i]=a1*a2…*ai-1*ai+1*…an，

follow up:不能用除法

+ a. 假设有函数int[] getConnection(memberID)，结果是有序的，要求实现：
  + isFirstDegree(member1,member2)
  + isSecondDegree(member1,member2)
  + isThirdDegree(member1,member2)      
就是判断一度，二度，三度好友关系，是系统设计题，伪代码即可。

follow up：分布式下怎么做

+ b. tinyurl

follow up:问如何scala-out

###5. 埃塞俄比亚小伙
悲剧的一轮，小伙人很好，但英语比阿三还难懂，有史以表现最差的一次。

+ a. 给一个矩阵，followMatrix[i][j]==true，表示j影响了i。求influencer，即影响所有人，且不被任何人影响
+ b. 三角形问题，输入一些线段的长度，找出能形成三角形的三条线段

###6. 老美

表现最好的一轮，有相似的项目经验，聊的比较投机

+ a. max points on a line
+ b. 给int[] a,求int[] result。 其中`result[i]=a1*a2…*ai-1*ai+1*…an`，

follow up:不能用除法

