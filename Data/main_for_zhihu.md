<!-- File for BP tutorial -->

# Belief Propagation 速成备忘录

这玩意每隔两年都要忘，这次搞个备忘录。

主要内容来自《Factor Graphs and the Sum-Product Algorithm》以及《Understanding Belief Propagation and its Generalizations》。

## 1. Factor Graph

让我们假设有一系列变量$ x_1, x_2, \ldots, x_n \\$ ，其中每个变量$ x_i$ 都取值于一个有限符号集合$ A_i$ 。令$ g(x_1, x_2, \ldots, x_n)$ 为一个实值函数，这个函数的定义域即为

$$
\mathcal{S} = A_1 \times A_2 \times \ldots \times A_n
$$

其实$ g$ 就是联合概率分布函数。相应地，将会存在$ n$ 个边缘概率分布函数$ g_i(x_i)$ 。对于每个$ x_i$ ，$ g_i(x_i)$ 定义为$ g(x_1, x_2, \ldots, x_n)$ 对所有$ x_{j, j\neq i} $ 的求和。也就是

$$
g_i(x_i) = \sum_{x_1\in A_1}\sum_{x_2\in A_2}\ldots\sum_{x_{i-1}\in A_{i-1}}\sum_{x_{i+1}\in A_{i+1}}\ldots\sum_{x_n\in A_n} g(x_1, x_2, \ldots, x_n)
$$

这看起来太吓人了所以引入一个简化写法

$$
g_i(x_i) = \sum_{\sim x_i} g(x_1, x_2, \ldots, x_n)
$$

意思是对$ x_i$ 之外的所有变量求和。

很多时候联合概率分布函数可以写成一系列因子的乘积形式，即

$$
g(x_1, x_2, \ldots, x_n) = \prod_{j \in J} f_j(X_j)
$$

这里的意思是有$ J$ 个因子函数$ f_j$ ，每个因子函数$ f_j$ 都是一个函数，其定义域是$ X_j$ 。每个$ X_j$ 都是$ \{x_1, x_2, \ldots, x_n\}$ 的子集。


<!-- 居中本地图片 -->
<p align="center">
  <img src="https://raw.githubusercontent.com/Niurouxing/Markdown4Zhihu/master/Data/main/1.png" width="400" />
</p>