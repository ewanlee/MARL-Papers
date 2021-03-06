这篇论文主要提出了两种算法，分别是Deep Repeated Update Q-Learning (DRUQL, RUQL + DQN)以及Deep Loosely Coupled Q-Learning (DLCQL, LCQL + DQN)。

前者的主要思想是为了改善Q-Learning的overestimation问题，对于被采样（根据当前策略）概率高的action其进行Q值更新时步长更小，反之则更大。结合DQN算法的话其实就是对于不同的sample其进行梯度下降时候学习率各不一样。

后者是一个multi-agent的算法，其思想是借鉴了LCQL算法。具体来说，每个agent都维护一个独立度量并维护两套策略，当这个度量值比较高的时候，就执行独立策略；否则执行协作策略。这个独立度量是在训练过程中不断进行更新的，更新方式类似于资格迹，并且更新起点是那些reward为负值的状态。

对于后者这个算法，其实意思是说只要某一个状态收到了一个负反馈，就认为agent需要去增大它的协作意识。感觉这种想法不是很有道理，负反馈可能是说你这个状态依旧要执行独立策略，只不过agent现在学习到的策略不是很好，所以有了个负反馈。如果这时候去执行协作策略的话，反而在错误的道路上越走越远？