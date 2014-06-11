---
layout: post
title: Brain Teaser from Cracking the Coding Interview
description: 智力题
category: blog
---

以下从笔者的 [github](https://github.com/kunth/CrackTheCodingInterview/blob/master/6.x-BrainTeaser.md)中截取的，是对 [Cracking the Coding Interviewi(5th edition)](http://book.douban.com/subject/10436668/)中的第六章的题解。

有六题，都是面试中常见智力题。

### 6.1
> You have 20 bottles of pills. 19 bottles have 1.0 gram pills, but one has pills of weight 1.1 grams. Given a scale that provides an exact measurement, how would you find the heavy bottle? You can only use the scale once.

20个瓶子，有19个瓶子装的都是1克的药片，另外1个瓶子装的都是1.1克的药片，有一个能测量出精确重量的天平，如何只用一次天平，找到哪个瓶子装的是1.1克的药片(每个瓶子都有足够多的药片)。

#### 6.1 solution
Firstly, number the bottles as #1, #2, ..., #20
Secondly, as there is only one bottle that is 0.1 gram heavier than others, we can pick out different pills in that rule:

bottle #1, 1 pill

bottle #2, 2 pills
...
bottle #20, 20 pills

Add all of them above, and substract (1+2+...+20) = 210, e.g. the result is 1.1, then is the bottle #11 that have 1.1 grams pills.


给瓶子编号，1到20，对编号为x的瓶子取出x个药片，总和减去210，余数乘以10就是装这1.1克瓶子的编号。

### 6.2
> There is an 8x8 chess board in which two diagonally opposite corners have been cut off. You are given 31 dominos, and a single domino can cover exactly two squares. Can you use the 31 dominos to cover the entire board? Prove your answer (by providing an example or showing why it's impossible).

8 * 8的棋盘，对角线的两个角(1 * 1)被切去。诺骨牌是面积为2的矩形，能否用31个诺骨牌来覆盖被切去两个角的棋盘？

#### 6.2 solution:
Very skillful, color the chess to 32 white and 32 black, since the opposite corners must be the same color, so after removing such two corners, it may be 30 white and 32 black left. Any domino covers one black and one white, so it could be impossible.

很巧妙，给棋盘上色，32白32黑，因为是对角，所以颜色一定相同，假设是30白32黑，而每一块诺骨牌总是占一黑一白，所以不可行。

![chess](/images/chess.png)

### 6.3
> You have a five-quart jug, a three-quart jug, and an unlimited supply of water (but no measuring cups). How would you come up with exactly four quarts of water? Note that the jugs are oddly shaped, such that filling up exactly "half" of the jug would be impossible.

3夸脱和5夸脱的容器各一个，如何量出4夸脱的水

#### 6.3 solution:
Old question. I had seen it several years ago.

Firstly, fill 5-quart up. Then, pour 5-quart into 3-quart until it is full. At that time, it's 2 quart left in 5-quart jug.And then, empty the 3-quart and pour the left 2 quart into the 3-quart. Lastly, fill 5-quart jug up and pour it until the 3-quart jug full. At that time it's 4 quart left in 5-quart jug.

先把5夸脱杯子装满，倒到3夸脱杯子里，剩2夸脱。把3夸脱杯子清空，再把这2夸脱水倒倒3夸脱杯子里，把5夸脱杯子盛满水，将3夸脱杯子倒满，此时5夸脱杯子里剩下4夸脱水。

### 6.4
> A bunch of people are living on an island, when a visitor comes with a strange order: all blue-eyed people must leave the island as soon as possible. There will be a flight out at 8:00pm every evening. Each person can see everyone else's eye color, but they do not know their own (nor is anyone allowed to tell them). Additionally, they do not know how many people have blue eyes, although they do know that at least one person does. How many days will it take the blue-eyed people to leave?

有一群人生活在岛上，每天有一班飞机到岛上。有个奇怪的规矩，蓝眼睛的人得上飞机离开。每个人可以看见其他人眼睛的颜色，但是不知道自己眼睛的颜色。至少有一个人是蓝眼睛，问得过多少天，蓝眼睛的人才会乘飞机离开。

#### 6.4 solution:

经典题。和[白帽子黑帽子问题](http://www.jobdao.com/interview/interview_82.htm)一样。书上也有讲, 可以参考书上的解法，是一样的。

### 6.5
> There is a building of 100 floors. If an egg drops from the Nth floor or above, it will break. If it's dropped from any floor below, it will not break. You're given two eggs. Find N, while minimizing the number of drops for the worst case.

有100层的楼，一个鸡蛋从N层或者比N层大的楼层掉下来会摔破，而从比N层小的地方掉下来不会被摔破。给定2个鸡蛋，找到这样一个N，使得最坏的情况下最小化鸡蛋下落的次数。

#### 6.5 solution

首先理解题意。最小化鸡蛋下落的次数是这样理解，比如鸡蛋在10层以上会摔破，那么我们要找到这个特定的10，可以把一个鸡蛋先仍倒1层，没破，再仍倒第二层，也没有破，一直仍倒第10层，破了，噢我们用1个鸡蛋测了10次才找到这个10(恩对，另外一个鸡蛋没派上用场)。当然我们也可以先丢到第5层，鸡蛋没破，让回我们在丢到第10层，鸡蛋破了，那么我们知道这个N应该在6到10之间，这个时候用第二个鸡蛋，从6开始试，一直到10，这样我们只测了6次，就测出了N==10。

题目就是说在最坏的情况下，用两个鸡蛋，用最少的测量次数，得到这个N

如果要理解“最坏情况”，这里就有个“负载均衡”的概念，无论第一个鸡蛋在那一层上摔破，第一个鸡蛋的测试次数+第二个鸡蛋的测试次数是一样的。

按照这个概念，假设第一个鸡蛋第一次尝试应该仍在第x层，如果第一个鸡蛋没摔破，用“负载均衡”的概念，第一个鸡蛋第二次尝试的时候应该在y层。后面我们就先不假设，先分析这个简单情况。如果第一个鸡蛋第一次尝试就破了，那么第二个鸡蛋应该从第1层往第x层尝试，最坏情况下，第二个鸡蛋尝试要到了第x-1层，两个鸡蛋一共尝试了x次。好，如果第一个鸡蛋第一次尝试没破，第二次尝试在第y层破了，那么第一个鸡蛋总共掉了两次，这时第二个鸡蛋应该从第x+1层开始尝试，最坏情况下尝试到y-1层，两个鸡蛋总共尝试了

**2+(y-1)-(x+1)+1 = y-x+1**

恩，回到“负载均衡”概念，最坏情况下，无论鸡蛋1尝试了多少次，鸡蛋1和鸡蛋2的总尝试个数是相等的，所以应该有

**y-x+1 = x 推出 y = 2x-1**

即如果鸡蛋i次尝试步进为z，下一次步进应该为z-1了, 一直到最后步进为1。也就是说，第一次在x层，第二次在x+x-1层，第三次在x+x-1+x-2层了，即

**x + x-1 + x-2 + ... + 1 = 100. 解得 x = 14**

即鸡蛋1先尝试14层，没破的话尝试27，再没破的话尝试39，再50...
如果鸡蛋1在第二次尝试即27层破了，鸡蛋2从14+1开始，最坏情况下尝试到26(顺便验证下，鸡蛋1的两次加上鸡蛋2从15到26的12次，正好14), 其他情况以此类推...

### 6.6
> There are 100 closed lockers in a hallway. A man begins by opening all 100 lockers. Next, he closes every second locker. Then, on his third pass, he toggles every third locker (closes it if it is open or opens it if it is closed). This process continues for 100 passes, such that on each pass i, the man toggles every ith locker. After his 100th pass in the hallway, in which he toggles only locker #100, how many lockers are open.

有100个门，第一次把100个门都打开，第二次把2的倍数的门都关上，第三次把3的倍数的门都置反，即第i次对编号为i的倍数的所有门，如果是关的，则打开，如果是打开的，则关上。问这样操作100次后，打开的门有几个

#### 6.6 solution

首先想了一下，编号为x的门，应该和x的质因数有关，比如编号为1的门，只有在第1次打开，之后不会再被操作，而编号为2和3的门，在第一次操作被打开后，分别在第二次和第三次操作中被关上，从此不再被操作。
这样的话，可以把每个数的质因数与1和其本身(如果都没有重复的话)都列出来，如下：

1: `1`

2: `1, 2`

3: `1, 3`

4: `1, 2, 4`

...

100: `1, 2, 4, 5, 10, 20, 25, 50, 100`

这样分别数一数每个数的因数个数，如果是奇数个的话，门最后应该是开的，偶数个的话，门就应该是关着的。

到此为止，已经解决一大半了，但是问题还是略微复杂，因为还要统计，如果是10000道门或者更多的话，复杂度还是很高。

再仔细想想，只有平方数才有奇数个因数，比如4，只有1,2,4，而非平方数，总有X=Y×Z，所以是偶数，而对于平方数，比如4，2只贡献了1次，所以是奇数个。那么这题就转换为100以内的平方数，那就是1到10的平方，有10个，所以最后是10道门是开的。

最后提一下，这题和常见的N!中有多少个0的也有点联系，N!是从某个特殊的平方数入手的。什么？你没有见过N!中算0的个数的，那么我随便google一个出来了，[点此查看](http://blog.csdn.net/u013081425/article/details/19805923 "算N!中0的个数")


