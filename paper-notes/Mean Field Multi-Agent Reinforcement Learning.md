这篇论文将平均场理论应用到multi-agent中来，平均场理论简要概括来说就是在一个有多个个体互相之间存在影响的环境中，一个个体
与其他所有个体之间的相互影响等价于该个体与其邻近区域内的个体的平均值所形成的虚拟个体之间的相互影响。相当于把一个一对多的关系
转换成了一个一对一的关系，multi-agent问题就变成了一个two-agent问题。

这个想法听起来就很有道理啊，说实话整篇论文都是数学证明，我基本没怎么看（主要是不想看），但是一般这种论文首先不管实验结果如何，
其理论基础就很扎实。而且比较好的一点在于，最后的算法是很简单明了的，简单来说就是一般单一agent的Q-learning或者Policy Gradient方法
输入一般是一个`(s, a)`对，因为多agent问题被转化为two-agent问题了，所以现在的输入就不是`(s, a, a_1, a_2,...)`而是变成了
`(s, a, \bar(a))`，这个平均action就是其他邻近agent的算术平均值。

然后论文提出了两种算法，一种是与Q-Learning进行结合，另外一种是与Actor-Critic结合。对于第一种方法，其policy是采用玻尔兹曼策略。
MF-Q算法如下：

![](http://o7ie0tcjk.bkt.clouddn.com/dwqg5.jpg)

算法中涉及到的公式11和12如下：

![](http://o7ie0tcjk.bkt.clouddn.com/e0xfo.jpg)


MF-AC如下：

![](http://o7ie0tcjk.bkt.clouddn.com/nhttn.jpg)
