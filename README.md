# 简介
**探索人工智能** 是一个自主学习项目，围绕项目主题了解什么是智能，有哪些人工智能的应用，以及如何实现人工智能。该项目记录学习过程中的想法，寻找到的资料，动手实践的成果。

# 学习经历
## 2019年
### 7月
- [写给正在填报志愿并对CS/AI感兴趣的考生们-2019](https://zhuanlan.zhihu.com/p/68474477)
- 《Deep Learning》[Chapter 5 - Machine Learning Basics](http://www.deeplearningbook.org/contents/ml.html) / 第5章-机器学习基础 
- 《Deep Learning》[Chapter 9 - Convolutional Networks](http://www.deeplearningbook.org/contents/convnets.html) / 第9章-卷积网络，不适合初学者看，不过其中一节讲述了视觉皮层的结构和功能比较有趣。
- 《Neural Networks and Deep Learning》[Chapter 6 - Deep Learning](http://neuralnetworksanddeeplearning.com/chap6.html) / 第6章-深度学习，通过讲解卷积神经网络学习深度学习，适合初学者学习。
- [ImageNet Classification with Deep Convolutional Neural Networks](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf) 2012年这篇论文引发了深度学习的热潮，值得了解下。
- 《Neural Networks and Deep Learning》[Learning with gradient descent](http://neuralnetworksanddeeplearning.com/chap1.html#learning_with_gradient_descent) / 学习梯度下降，简洁易懂。
- 《Neural Networks and Deep Learning》[Chapter 2 - How the backpropagation algorithm works](http://neuralnetworksanddeeplearning.com/chap2.html) / 第2章-向后传播算法，训练神经网络的基本算法，必须得了解。
- 《Neural Networks and Deep Learning》[Chapter 3 - Improving the way neural networks learn](http://neuralnetworksanddeeplearning.com/chap3.html) / 第3章-改善神经网络学习的方法，在该章节中了解交叉熵损失函数，正则化的概念以及一些可用的方法包括权重衰减(L2 正则化)、L1 正则化、Dropout。
- [Keras](https://www.tensorflow.org/guide/keras) TensorFlow官网的 Keras 入门指南； Keras 是一个用于构建和训练深度学习模型的高级API；学习Keras为接下来动手实践做准备。
- [机器学习科研的十年](https://zhuanlan.zhihu.com/p/74249758)，对要走机器学习之路的同学应该能带来一些启示。
- [Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist)，了解了下 Fashion-MNIST 数据集，在卷积网络的练习中使用。
- [What is a batch-norm in machine learning?](https://www.quora.com/What-is-a-batch-norm-in-machine-learning)，在做卷积网络练习的时候为了提升模型在 Fashion-MNIST 的准确度，了解到有个叫 Batch Normalization 的方法可以提升模型效果，比起数据增强等其它的提升方法，Batch-Norm 更我让感兴趣，故学习学习。
- [Batch normalization in Neural Networks](https://towardsdatascience.com/batch-normalization-in-neural-networks-1ac91516821c)，简单介绍 Batch Nomalization 的文章。
- [Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift](https://arxiv.org/abs/1502.03167)，Batch Normalization 原论文，拜读一下。
- [GPU Support](https://www.tensorflow.org/install/gpu)，Tensorflow 的 GPU 支持。 在2013年的 Macbook Pro 上使用 CPU 训练实在是太慢了，Fashion-MNIST 训练30轮需要半小时，把我暗影精灵3上的 Nvidia GTX 1060 利用起来。
### 8月
- [An Introduction to AdaGrad](https://medium.com/konvergen/an-introduction-to-adagrad-f130ae871827)，在做卷积网络练习的时候采用了 AdaGrad 进行模型的训练；AdaGrad 的论文([Adaptive Subgradient Methods for
Online Learning and Stochastic Optimization](http://www.jmlr.org/papers/volume12/duchi11a/duchi11a.pdf))太长了，所以找了篇入门文章简单了解下。
- TensorFlow - Low Level API：[Introduction](https://www.tensorflow.org/guide/low_level_intro)、[Tensors](https://www.tensorflow.org/guide/tensors)、[Variables](https://www.tensorflow.org/guide/variables)、[Graphs and Sessions
](https://www.tensorflow.org/guide/graphs)、[AutoGraph: Easy control flow for graphs
](https://www.tensorflow.org/guide/autograph)；TensorFlow 的低级 API 入门；卷积网络练习的第一阶段已经达到了在 Fashion-MNIST 数据集上取得 93% 以上准确度的目标，开始进入练习的第二阶段，使用 TensorFlow 低级 API 实现第一阶段创建的模型。
- [What's the difference of name scope and a variable scope in tensorflow?](https://stackoverflow.com/questions/35919020/whats-the-difference-of-name-scope-and-a-variable-scope-in-tensorflow)，在使用 TF 的变量时，没搞清楚定变量的命名空间的问题。
- 《动手学深度学习》[softmax回归](https://zh.gluon.ai/chapter_deep-learning-basics/softmax-regression.html)，回顾下 Softmax，在卷积网络练习种得自己实现下。
- [TensorFlow Debugger](https://www.tensorflow.org/guide/debugger)，在实现 softmax 时候，发现输出得值总是 nan， 所以了解了如何调试 TensorFlow，期间尝试了 TensorBoard 和 CLI 两个调式方式，CLI 的方式比较好用些。 
- [How to Implement Minibatching in Tensorflow](http://deeplearnphysics.org/Blog/minibatch.html)，如何在 TensorFlow 中实现小批量的样本输入。
- [Data Input Pipeline Performance](https://www.tensorflow.org/guide/performance/datasets)，TensorFlow 的数据输入管道。

# 练习
## 卷积网络练习
练习分3个阶段：
- 第一阶段通过 Keras 的高级 API 搭建网络模型，使得模型在 Fashion-MNIST 数据集上取得 93% 以上的测试准确度；
- 第二阶段是将第一阶段的模型使用 Tesnforlow 的低级 API 实现；
- 第三阶段是将第一阶段的模型使用纯 Python 实现。

[建模日志](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/README.md)，将建模过程记录下来。

第一阶段:
 - Keras 模型1 - [keras_model_1.py](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/keras_model_1.py)，准确度为 92.05%。
 - Keras 模型2 - [keras_model_2.py](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/keras_model_2.py)，准确度为 92.24%。
 - Keras 模型3 - [keras_model_3.py](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/keras_model_3.py)，准确度为 94.38%。

第二阶段：
  - TF 模型 - [tf_model.py](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/tf_model.py) 和  [tf_model_layers.py](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/tf_model_layers.py)
  
 第三阶段：
 已放弃。

# 机器学习在线课程
- [Neural Networks and Deep Learning](http://neuralnetworksanddeeplearning.com)
- [Deep Learning](http://www.deeplearningbook.org)
- [机器学习速成课程](https://developers.google.com/machine-learning/crash-course/?hl=zh-cn)
- [动手学深度学习](https://zh.gluon.ai/)
- [Elements of AI](https://course.elementsofai.com/)

# 应用
- [机甲大师 RoboMaster S1](https://www.dji.com/cn/robomaster-s1?site=brandsite&from=homepage) - 大疆机器人， 6 类人工智能编程模块。
- [Runway ML](https://runwayml.com/) - Machine learning for creators；一个工具类产品，有多种机器学习的模型，比如图像生成，动作捕捉等，用于设计创造类的工作。

# 问题 & 想法
- 人工智能的核心构件有哪些？[#2](https://github.com/kai-zhong/discover-intelligence/issues/2)
- 梯度降下算法中求最小值的想法[#3](https://github.com/kai-zhong/discover-intelligence/issues/3)
