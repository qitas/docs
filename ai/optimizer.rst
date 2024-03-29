
.. _optimizer:

optimizer
===============

梯度下降法
-----------

梯度下降法(Gradient Descent)最基本的一类优化器，目前主要分为三种：标准梯度下降法(GD, Gradient Descent)、随机梯度下降法(SGD, Stochastic Gradient Descent) 及批量梯度下降法(BGD, Batch Gradient Descent)。

标准梯度下降法主要有两个缺点:

训练速度慢：在应用于大型数据集中，每输入一个样本都要更新一次参数，且每次迭代都要遍历所有的样本。会使得训练过程及其缓慢，需要花费很长时间才能得到收敛解。
局部最优解：所谓的局部最优解就是鞍点，落入鞍点，梯度为0，使得模型参数不在继续更新。
BGD
每次权值调整发生在批量样本输入之后，而不是每输入一个样本就更新一次模型参数，这样就会大大加快训练速度

批量梯度下降法比标准梯度下降法训练时间短，且每次下降的方向都很正确。

SGD
-----------

SGD根据的是一整个数据集的随机一部分

虽然SGD需要走很多步的样子，但是对梯度的要求很低（计算梯度快）。而对于引入噪声，大量的理论和实践工作证明，只要噪声不是特别大，SGD都能很好地收敛。

应用大型数据集时，训练速度很快。比如每次从百万数据样本中，取几百个数据点，算一个SGD梯度，更新一下模型参数。相比于标准梯度下降法的遍历全部样本，每输入一个样本更新一次参数，要快得多。

SGD在随机选择梯度的同时会引入噪声，使得权值更新的方向不一定正确。此外，SGD也没能单独克服局部最优解的问题。

动量优化法
-----------

动量优化方法是在梯度下降法的基础上进行的改变，具有加速梯度下降的作用。一般有标准动量优化方法Momentum、NAG（Nesterov accelerated gradient）动量优化方法。

使用动量(Momentum)的随机梯度下降法(SGD)，主要思想是引入一个积攒历史梯度信息动量来加速SGD。

牛顿加速梯度（NAG, Nesterov accelerated gradient）算法，是Momentum动量算法的变种。

自适应学习率优化算法
----------------------

自适应学习率优化算法针对于机器学习模型的学习率，传统的优化算法要么将学习率设置为常数要么根据训练次数调节学习率。极大忽视了学习率其他变化的可能性。然而，学习率对模型的性能有着显著的影响，因此需要采取一些策略来想办法更新学习率，从而提高训练速度。

目前的自适应学习率优化算法主要有：AdaGrad算法，RMSProp算法，Adam算法以及AdaDelta算法。

Adam算法
-----------

首先，Adam中动量直接并入了梯度一阶矩（指数加权）的估计。其次，相比于缺少修正因子导致二阶矩估计可能在训练初期具有很高偏置的RMSProp，Adam包括偏置修正，修正从原点初始化的一阶矩（动量项）和（非中心的）二阶矩估计。

目前，最流行并且使用很高的优化器（算法）包括SGD、具有动量的SGD、RMSprop、具有动量的RMSProp、AdaDelta和Adam。在实际应用中，选择哪种优化器应结合具体问题；同时，也优化器的选择也取决于使用者对优化器的熟悉程度（比如参数的调节等等）。
