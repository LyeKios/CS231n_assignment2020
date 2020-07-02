# CS231n_assignment2020
CS231n: Convolutional Neural Networks for Visual Recognition.

# 用做笔记 知识点&小记录

## 2020.7.1

### Lecture-1
    计算机视觉概述，历史背景
### Lecture-2
    K近邻，线性分类I
    L1 distance:曼哈顿距离（对应点绝对值差之和）     适用于明确含义值
    L2 distance:D2(I1,I2)=sqr(sum((i1-i2)**2))     适用于几何距离
### Lecture-3
    线性分类II，高级表示，图像特征优化，随机梯度下降
    支持向量机：铰链损失函数Multi-SVM Loss:分类错误的指标与正确得分差值，与0的较大者累加 L=sum（max（0，sj-si+1))   当正确类别分数较高且显著时，
        这个损失函数会趋于0，是一个校验损失函数，惩罚分类易混淆的类得分。
    L1 正则：权重绝对值相加
    L2 正则：权重平方相加  
    Lamda过大时惩罚过度造成权重归零，过小时惩罚太轻造成过拟合。即惩罚大时训练Loss会增大，但是可能增强模型实用性。
    SoftMax classifier: 先求exp，再归一化计算分类概率
    交叉熵损失函数/负对数损失函数：Loss=-log(P)  P为类预测概率 y=logx为递减且属于（-无穷，0），所以加一个负号翻转为正  
        目的：将多类别概率相乘简化为对数相加，Loss越少说明预测效果越好，正确类别越突出。
    梯度下降：解析解W_grad = eval_grad(loss, data, weights) 反向传播更新权重。
    SGD随机梯度下降容易陷入局部最优。
    动量下降会有惯性。
    更新权重时，全部数据每轮迭代很不经济，所以引出mini-Batch批的概念，小碎步快速迈进。
    特征工程：提取图片特征，用新的高维向量代替图片用来进行分类训练，提高分类效率和效果。由卷积神经网络完成这部分工作，卷积核决定的特征提取。
        优势：特征表达性更好、运算量得以减少、语义特征得到更大重视。
    特征包括：颜色通道、直方图特征、BoW、等
## 2020.7.2
### Lecture-4
    传统视觉方法：HOG、SIFT等特征提取
    深度学习方法：大数据支持下的端到端自提取特征
    全连接神经网络FCN多层感知机MLP
    激活函数带来非线性，否则多层的权重W1W2W3相乘可用一个W'代替，即与单层感知机无异。
    反向传播 局部求导梯度   加法梯度复制，乘法梯度交换，Max梯度路由只走权重最大
    雅可比矩阵：稀疏矩阵，仅在对角线有非零值的矩阵。
    隐含层将非线性数据转换为线性线性可分数据，在最后进行线性分类。一个神经元可看作一个线性边界。
    单层感知机在神经元个数足够时可以拟合任何问题，但是宽泛且浅，运算上不经济。通过添加层数可以更好发挥激活函数的作用。
