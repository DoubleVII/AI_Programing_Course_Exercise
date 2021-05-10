# 信息系统
信息系统或资讯系统（Information Systems），从技术上说就是为了支持组织决策和控制而收集（或获取）、处理、存储、分配信息的一组相互关系的组件。主要有五个基本功能，即对信息的**输入、存储、处理、输出和控制**。

作为信息系统的核心技术和重要基础设施，本题目要求实现一个简易的数据库管理系统，能够体现上述五个基本功能。

## 信息存储
数据库信息可以简单地存储在内存中，也可以基于文件进行存储。

你可以选择在程序初始化时从文件中读取全部的数据到内存中，在退出程序时将内存中的数据保存回文件。更加安全、减少内存开销的做法是数据库的增删改查操作都基于文件进行，仅仅在内存中存放数据库程序而不存放数据。也可以选择读取部分数据到内存中，以减少频繁的文件读写。

在进行文件的存储时，你可能需要根据数据类型设计相应的数据结构，以方便程序进行读写或加速数据库的效率。

## 信息输入、输出和控制
在数据库系统中，信息的输入、输出和控制被称为增删改查操作，即增加（Create）、删除（Delete）、修改（Update）和查询（Read）。

你的程序应该支持上述四种指令。例如，你的程序用于保存个人信息（姓名、性别和年龄），如果你的程序在命令行中运行，那么可以定义一种增加指令`create <name> <gender> <age>`，表示向数据库中添加一条个人信息数据。程序启动后，在命令行输入`create zhangsan male 24`即可添加张三（zhangsan）的个人信息到数据库中。 其他的命令也是类似的。

这些命令的格式你可以自行设计，每种类型的操作可以对应多条命令以增加程序的灵活性，比如定义`createn`表示一次性添加多条信息。

## 信息的处理
根据数据库具体存储的信息，可以对信息进行不同的处理。这里要求同学们使用在课程中学习的相关算法对数据进行处理。

## 数据
我们提供了一些可用的数据，你可以选择其中的一种来构建你的数据库。如果你对我们提供的数据不感兴趣，可以自行构建数据，在这种情况下，你可能需要编写脚本用于数据的抓取和处理。

### Coursera课程数据
总共379个课程，每行包括3部分内容：课程名\t课程简介\t课程详情。[下载地址](https://pan.baidu.com/s/1sXec_tav6FLznfXf3Tbu-Q)，提取码`9squ`。

信息处理任务：
1. 文档内容进行处理（如分隔标点符号，大小写转换等），方便之后的相似度分析。
2. 选择合适的算法，分析给定课程与各个课程之间的相似度。你的程序应该接受一个用户输入的课程名称，输出与之最相似的k门课程，其中k由你自己决定。

你可能需要使用nltk、gensim等Python库。具体的处理算法可以参考[这里](https://www.52nlp.cn/%E5%A6%82%E4%BD%95%E8%AE%A1%E7%AE%97%E4%B8%A4%E4%B8%AA%E6%96%87%E6%A1%A3%E7%9A%84%E7%9B%B8%E4%BC%BC%E5%BA%A6%E4%B8%89)。

### 人脸识别数据
[Faces94数据集](https://cmp.felk.cvut.cz/~spacelib/faces/faces94.html)包含3060张人脸图片，图片大小为200*180。

信息处理任务：
1. 数据获取与预处理。可自行划分训练集和测试集。
2. 问题分析与建模。运用所学知识对人脸识别问题进行建模（用数学公式表达如何识别出是哪一个人的面部）。建议以KNN(最近邻分类)为基础，探索其他更好的方法。
    * 要判断图片$X^{\prime}$属于哪一个类别，将$X^{\prime}$与数据集中的其他图片一一比较，找到$X_i$使得$\|X^{\prime}-X_i\|$最小，则$X^{\prime}$的类别应该与$X_i$的类别相同。
    * 可以考虑对$X$做一些变换$f(X)$，来取得更好的效果，即求$\|f(X^{\prime})-f(X_i)\|$的最小值。
3. 模型测试与评价。在测试集上测试模型的准确率。
4. 可视化。例如显示人脸图片$X$和变换后的图片$f(X)$。

可以使用Opencv处理图像数据，安装方法`pip install opencv-python`，使用方法可以参考[这里](https://blog.csdn.net/CDQ928/article/details/75137350)。

可视化推荐使用matplotlib库。

### 中文对话情感分类数据
[基于中文的预分词后的对话数据](https://github.com/z17176/Chinese_conversation_sentiment)（空格分词），情感分为两类。

信息处理任务：
1. 基于数据中给定的字符级表示，使用相关算法收集和情感极性相关的“关键词”，分析这些结果是否符合预期，并基于关键词进一步设计分类方案。
2. 尝试从特征表示的角度，对第一阶段的分类设计进行性能改进。请尝试分析原方案特征表示的缺陷和你的针对改进，并通过实验结果比较验证你的分析。
3. 从分类模型性能的角度进行优化（可以参考文献）。同样请尝试分析原分类方案可能存在的缺陷和自己选用的改进模型的优势，并通过实验结果比较验证你的分析。

相关的[参考文献](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.471.2307&rep=rep1&type=pdf)。

## 注意事项
在本题目中，信息存储、输入、输出和控制部分着重于程序设计，信息处理部分着重于相关算法的应用。如果在设计时有一定的困难，这两部分可以选择一个部分作为重点，即只完成一个方面的要求即可。