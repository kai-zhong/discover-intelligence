# 建模日志
## 阶段一：使用 Keras 高级 API 创建模型
### 模型1
- 第一个模型简单起见，能让模型能正常运行就成；因此网络结构为：输入层、一个卷积层、一个MaxPooling层、一个 Dropout 层、一个稠密层、输出层；卷积层使用 ReLU 做为激活函数，稠密连接层和输出层使用 Sigmoid 作为激活函数，最后使用 CrossEntropy 做为损失函数，使用随机梯度下降进行模型的训练方法；在该模型下准确率为89.42%。参见模型代码 [96ec43d - keras_model.py](https://github.com/kai-zhong/discover-intelligence/blob/96ec43d97740f59f81405845e80f6aebd1700bd2/cnn_practice/keras_model.py)
- 在上一个简单模型基础上调整参数很难超过90%的准确度，所以把网络结构做了调整，使用了两个卷积层，两个稠密层并将激活函数改为ReLU，改变网络结构的同时将参数规模扩大后，达到了90.97%的精确度，算是前进了一小步。参见模型代码 [8239e08 - keras_model.py](https://github.com/kai-zhong/discover-intelligence/blob/8239e08077dba39ef9da7c30b40974cbd8a50e9a/cnn_practice/keras_model.py)
- 在参考其它模型结构的时候了解到 Batch Normalization，然后加以应用后，效果感人，训练速度提升很快，在 Fashion-MNIST 的准确度达到了91.48%，离92%不远了，胜利在望，加油加油～～。参见模型代码 [dd46a4e - keras_model.py](https://github.com/kai-zhong/discover-intelligence/blob/dd46a4e629b76acdaeda1c450cfde6dd676c711a/cnn_practice/keras_model.py)
- 在模型 [dd46a4e - keras_model.py](https://github.com/kai-zhong/discover-intelligence/blob/dd46a4e629b76acdaeda1c450cfde6dd676c711a/cnn_practice/keras_model.py) 上将训练次(Epochs)数从15改为30后，准确度达到了91.90%，还有0.1%就能完成第一阶段的目标了～～
- 将训练次数从30改为50后，达到了92.05%的准确度，第一个模型算是完成了，共花费了2天的时间，也不算难。参见模型代码 [keras_model_1.py](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/keras_model_1.py)
- 第一阶段原本是计划将模型达到92%的精确度就进入第二阶段，不曾想很快就达到了，觉得有点过于简单，且似乎觉得模型不是很简洁，所以改变第一阶段的目标，实现三个不同网络结构的模型都达到92%的准确度，这样一来能更好的从练习中学习更多的知识，获得更多的经验。
### 模型2
- 构建第二个模型特意避免使用 Batch Normalization 来提升模型效果，而是通过扩大参数规模来提升，参考了 [ImageNet Classification with Deep Convolutional Neural Networks](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf) 这篇经典论文中网络模型参数的配置，并采用了 Adagrad 做为训练方法，最终第二个模型的准确度达到了 92.24%，着实让人惊喜，原本以为不使用 Batch-Norm 可能只会勉强达到 92% 的准确度。参见模型代码  [keras_model_2.py](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/keras_model_2.py)
### 模型3
- 构建第三个模型的时候决定再次改变下第一阶段的目标，改为使模型的准确度达到93%，因为提高准确度同样需要进行更多的尝试，与应用更多的方法。
- 第三个模型同时使用了 Batch Normalizatin 和 更大规模的参数，使得准确度提高到了92.59%。参见模型代码 [02f6a19 - keras_model_3.py](https://github.com/kai-zhong/discover-intelligence/blob/02f6a19ae329539241ee8c9b2277461907e20791/cnn_practice/keras_model_3.py)
- 将两个卷积层的过滤器数量增大一倍，准确度达到了 92.63%。参见模型代码 [d66815e - keras_model_3.py](https://github.com/kai-zhong/discover-intelligence/blob/d66815ecde8deb7943dd999ff04e4a7577d33918/cnn_practice/keras_model_3.py)
- 将模型从两个卷积层增加四个，准确度达到了 92.91%，深度模型的效果明显~，离 93% 不远了。 参见模型代码 [8bd51c3 - keras_model_3.py](https://github.com/kai-zhong/discover-intelligence/blob/8bd51c3cab107794f5b3dfe7470459b4a94ef636/cnn_practice/keras_model_3.py)
- 将模型从四个卷积层减少至三个，同时将两个稠密层的参数从 2048 减少至 1024，同样达到了 92.91% 的准确度。 参见模型代码 [9f09480 - keras_model_3.py](https://github.com/kai-zhong/discover-intelligence/blob/9f09480c1614b717275dd14a1791dec7d6accc9d/cnn_practice/keras_model_3.py)
- 在卷积层之后加上 Batch Normalization，并将训练次数从 50 增加到 100，模型达到了 93.11% 的准确度，可喜可贺啊，再调调说不定都能达到 94% ；不给过觉的目前模型看上去不是很简洁，再调整下。参见模型代码 [3e7b56c - keras_model_3.py](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/keras_model_3.py)
- 增加了一个卷积层，训练方法从 AdaGrad 换成 SGD，学习率为 TensorFlow 默认的 0.01，模型用了较短的训练时间就达到了 93% 以上的准确度，最好的时候达到了 93.87%，真是惊讶不已，通过调整学习率能有效的提升模型效果，再继续调整下模型争取到达 94%。参见模型代码 [1c9b863 - keras_model_3.py](https://github.com/kai-zhong/discover-intelligence/blob/1c9b8630f405f08d71f76ea6c792c5237e2e87a9/cnn_practice/keras_model_3.py)
- 将输出层之前的一个 Batch Normalization 移除掉后，在 Epoch 94/100 时刚好达到了 94.00% 的准确度，实属侥幸啊。最后再调一波，使模型稳定得达到 94% 就结束第一阶段，✌。参见模型代码 [2add9b0 - keras_model_3.py](https://github.com/kai-zhong/discover-intelligence/blob/2add9b074efdfb0cd0bfef5e8cb63ea6ec62d2b8/cnn_practice/keras_model_3.py)
- 经过一番调整，模型终于能稳定的达到 94.00% 以上的准确了，最好的时候达到了 94.38%，且网络结构和参数规模均变小了；突破 94% 的关口主要的途径是解决训练集过拟合的问题，Dropout 还是比较有效的；虽然觉的还可以继续提升模型效果，但该练习的目标已经完全达到了，该进入下一阶段了。 参见最终模型代码 [kers_model_3.py](https://github.com/kai-zhong/discover-intelligence/cnn_practice/keras_model_3.py)
### 总结
最初只是想构建一个简单的卷积网络能正常的处理 Fashion-MNIST 数据集，就像 [模型1](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/keras_model_1.py) 只有一个卷积层；但最初的想法过于简单很快就实现了，这让我有些意犹未尽，就想尝试尝试更的深网络结构，在尝试后发现准确度有所提升了，超过了 90%，因为在只有一个卷积层的模型中，准确度很难超过90%， 通常只到 89% 左右；在不断地调整过程中，准确度不断地随之提升，激起了我达到更好结果的欲望，起先的目标是达到 92%，很快就实现了，然后 93%，最后 94%。其实这个过程是学了很多东西的，比如了解到了 Batch Normalization 和 Adagrad，都能提升模型效果，还实际感受到了模型参数规模过大会造成过拟合，Dropout 的使用能有效的缓解过拟合的问题。在不断尝试的过程中，能越来越感知到可以提升模型效果的方向，不过还是很缺乏理论上更有直觉的认识。总之整个过程花费差不多一星期的时间，收获很多，很满足，很开心。
  
## 阶段二：使用 TensorFlow 低级 API 实现第一阶段模型
- 刚开始的时候完全无从下手，不知道该先从什么地方实现模型，琢磨了一番后决定先从最简单的网络结构开始实现，让样本能够经过一个稠密层, 激活函数使用 softmax，能够正常输出即可。参见模型代码 [d72595f - tf_model.py](https://github.com/kai-zhong/discover-intelligence/blob/d72595f7482c03577b64dc3cced39f0a4e89955a/cnn_practice/tf_model.py) [d72595f - tf_model_layers.py](https://github.com/kai-zhong/discover-intelligence/blob/d72595f7482c03577b64dc3cced39f0a4e89955a/cnn_practice/tf_model_layers.py)
- 弄了好几天终于正确实现了 softmax 和 crossentropy，这个过程中遇到了好些问题，比如权重初始化不合适会照成 softmax 的输出值为 inf 或 nan，还有些基本的矩阵计算问题（学艺不精导致），为了调试这些问题，学习了 TensorFlow Debugger；其它还完成了模型训练部分的功能，比如优化损失函数（优化器使用 TF 提供的 AdagradOptimizer，之后也不准备在该阶段自己实现了）和验证测试集。参见模型代码 [cccd8f7 - tf_model.py](https://github.com/kai-zhong/discover-intelligence/blob/7e9f47ac612c5492978aad21d5edc5d319afae3a/cnn_practice/tf_model.py) [cccd8f7 - tf_model_layers.py](https://github.com/kai-zhong/discover-intelligence/blob/7e9f47ac612c5492978aad21d5edc5d319afae3a/cnn_practice/tf_model_layers.py)
- 实现卷积层过程真是曲折，基于计算图构建模型在好些控制逻辑上不知道如何处理，主要是将图片切割成小块时的逻辑，切割完了得将所有小块合并成一个 Tensor， 方便进行矩阵运算。最后还是勉强实现了卷积层，不过感觉与 TensorFlow 提供的相比，性能要差一些。
### 总结
第二阶段的难度比想象的要大，全部自己实现算法是一个很大的工程，非常多的细节需要处理，最终自己实现了一小部分，比如卷积层、稠密层，其余的还是使用了 TensorFlow 提供的接口。自己实现的运算性能不如 TensorFlow 提供的好，还有比如 loss 的数值容易为 nan ，也不知其原因，排查起来非常的耗时，需要大量的知识。总之第二阶段的模型与第一阶段的模型3的结构是一样的，能够正常运行，但性能差的太多，精确度不知道能不能达到一样的结果，因为训练太慢了就不耐烦等了。参见模型代码 [tf_model.py](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/tf_model.py) [tf_model_layers.py](https://github.com/kai-zhong/discover-intelligence/blob/master/cnn_practice/tf_model_layers.py)

## 阶段三：使用纯 Python 实现第一阶段的模型
这个阶段我放弃了，第二阶段就花了近两星期的时间才实现了很小一部分。此外觉的有些偏离的学习的轨道，其实这个阶段是一个工程问题，与学习机器学习的理论来说，已经超纲了。
