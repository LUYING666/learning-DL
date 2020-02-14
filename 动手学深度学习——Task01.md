## Task01-线性回归
### 一.线性回归
#### 1.基本要素
以一个简单的房屋价格预测作为例子，假设价格只取决于房屋的面积和芳龄。
模型：$\hat{y}=x_1w_1+x_2w_2+b$
模型训练：1）训练数据
&ensp;&ensp;&emsp;&ensp;&ensp;&emsp;&emsp;2）损失函数：$L(w,b)=\frac{1}{n}\displaystyle\sum_{i=1}^n\frac{1}{2}(\hat{y}^n-y)^2$
&ensp;&ensp;&emsp;&ensp;&ensp;&emsp;&emsp;3）优化算法：小批量随机梯度优化下降（mini-batch stochastic gradient descent）
模型预测：
#### 2.总结
当数据样本数为n,特征数为d时，线性回归的矢量计算表达式$\boldsymbol{\hat{y}} = \boldsymbol{X} \boldsymbol{w} + b$，其中模型输出$\boldsymbol{\hat{y}} \in \mathbb{R}^{n \times 1}$，批量数据样本特征$\boldsymbol{X} \in \mathbb{R}^{n \times d}$，权重$$\boldsymbol{w} \in \mathbb{R}^{d \times 1}$，偏差$b \in \mathbb{R}$，批量数据样本标签$ $\boldsymbol{y} \in \mathbb{R}^{n \times 1}$。设模型参数$\boldsymbol{\theta} = [w_1, w_2, b]^\top$，重写损失函数：$L(\boldsymbol{\theta})=\frac{1}{2n}(\boldsymbol{\hat{y}}-\boldsymbol{y})^\top(\boldsymbol{\hat{y}}-\boldsymbol{y})$。小批量随机梯度下降的迭代步骤将相应地改写为$\boldsymbol{\theta} \leftarrow \boldsymbol{\theta} -   \frac{\eta}{|\mathcal{B}|} \sum_{i \in \mathcal{B}}   \nabla_{\boldsymbol{\theta}} L^{(i)}(\boldsymbol{\theta})$，其中$\eta$为学习率，$|\mathcal{B}|$代表每个小批量中的样本个数（批量大小，batch size）。
#### 二.Softmax与分类模型
softmax回归跟线性回归一样将输入特征与权重做线性叠加。与线性回归的一个主要不同在于，softmax回归的输出值个数等于标签里的类别数。
softmax运算符（softmax operator）将输出值变换成值为正且和为1的概率分布：$\hat{y}_1, \hat{y}_2, \hat{y}_3 = \text{softmax}(o_1, o_2, o_3)$
其中$\hat{y}_j = \frac{ \exp(o_j)}{\displaystyle\sum_{i=1}^3 \exp(o_i)},\quad$易看出$\hat{y}_1 + \hat{y}_2 + \hat{y}_3 = 1$且$0 \leq \hat{y}_1, \hat{y}_2, \hat{y}_3 \leq 1$。
#### 1.总结
给定一个小批量样本，其批量大小为$n$，输入个数（特征数）为$d$，输出个数（类别数）为$q$。设批量特征为$\boldsymbol{X} \in \mathbb{R}^{n \times d}$。假设softmax回归的权重和偏差参数分别为$\boldsymbol{W} \in \mathbb{R}^{d \times q}$和$\boldsymbol{b} \in \mathbb{R}^{1 \times q}$。
softmax回归的矢量计算表达式为：
$$\begin{aligned} \boldsymbol{o}&= \boldsymbol{X} \boldsymbol{W} + \boldsymbol{b}
\\\boldsymbol{\hat{Y}} &= \text{softmax}(\boldsymbol{o})
\end{aligned}$$
#### 2.交叉熵损失函数：
假设训练数据集的样本数为$n$，交叉熵损失函数定义为
$$L(\boldsymbol{\Theta}) = -(1/n)  \sum_{i=1}^n \log \hat y_{y^{(i)}}^{(i)}$$
模型预测：使用准确率（accuracy）来评价模型的表现。它等于正确预测数量与总预测数量之比。
### 三.多层感知机
多层感知机在输出层与输入层之间加入了一个或多个全连接隐藏层，并通过激活函数对隐藏层输出进行变换。

#### 2.激活函数
1.ReLU（rectified linear unit）函数提供了一个很简单的非线性变换。给定元素$x$，该函数定义为
$$\text{ReLU}(x) = \max(x, 0)$$
2.sigmoid函数可以将元素的值变换到0和1之间：
$$\text{sigmoid}(x) = \frac{1}{1 + \exp(-x)}.$$sigmoid函数在早期的神经网络中较为普遍，但它目前逐渐被更简单的ReLU函数取代。
3.tanh（双曲正切）函数可以将元素的值变换到-1和1之间：
$$\text{tanh}(x) = \frac{1 - \exp(-2x)}{1 + \exp(-2x)}= \frac{2}{1 + \exp(-2x)}-1$$关于激活函数的选择：
ReLu函数是一个通用的激活函数，目前在大多数情况下使用。但是，ReLU函数只能在隐藏层中使用。
用于分类器时，sigmoid函数及其组合通常效果更好。由于梯度消失问题，有时要避免使用sigmoid和tanh函数。
在神经网络层数较多的时候，最好使用ReLu函数，ReLu函数比较简单计算量少，而sigmoid和tanh函数计算量大很多。
在选择激活函数的时候可以先选用ReLu函数如果效果不理想可以尝试其他激活函数。
