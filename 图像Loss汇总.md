# 图像loss汇总
***
```language
https://www.cnblogs.com/SuperLab/p/9837706.html
```


目前loss主要有以下几种：
1.针对图像的pixel2pixel的loss：L1,L2,SSIM，对以PSNR、SSIM为客观评价指标的问题贡献比较大。
- 特点：L2损失相比与L1损失收敛速度更快，但是其缺点是容易受离存点的影响。smooth L1和L1-loss函数的区别在于，L1-loss在0点处导数不唯一，可能影响收敛。smooth L1的解决办法是在0点附近使用平方函数使得它更加平滑。smooth L1 loss让loss对于离群点更加鲁棒，即：相比于L2损失函数，其对离群点、异常值（outlier）不敏感，梯度变化相对更小，训练时不容易跑飞。SooothL1Loss其实是L2Loss和L1Loss的结合，它同时拥有L2 Loss和L1 Loss的部分优点。当预测值和ground truth差别较小的时候（绝对值差小于1），梯度不至于太大。（损失函数相较L1 Loss比较圆滑）当差别大的时候，梯度值足够小（较稳定，不容易梯度爆炸）。

损失函数size_average=True or False
在pytorch中，所有的损失函数都带这个参数，默认设置为True。
当size_average为True的时候，计算出来的结果会对mini-batch取平均。反之，为False的时候，那算出来的绝对值不会除以n。




![16000487451.png](0)
***
- 常见易混概念总结

假设X是n维的特征 [公式]

L2范数： [公式]

1. L2损失函数(MSE)
L2范数损失函数，也被称为最小平方误差（LSE）。它是把目标值 [公式] 与估计值 [公式] 的差值的平方和最小化。一般回归问题会使用此损失，离群点对次损失影响较大。

2. L1损失函数（MAE）
也被称为最小绝对值偏差（LAD），绝对值损失函数（LAE）。总的说来，它是把目标值 [公式] 与估计值 [公式] 的绝对差值的总和最小化。

3. 二者对比
与最小平方相比，最小绝对值偏差方法的鲁棒性更好。因为L2范数将误差平方化（如果误差大于1，则误差会放大很多），模型的误差会比L1范数大的多，因此模型会对这个样本更加敏感，这就需要调整模型来最小化误差。如果这个样本是一个异常值，模型就需要调整以适应单个的异常值，这会牺牲许多其它正常的样本，因为这些正常样本的误差比这单个的异常值的误差小。

- 正则化
1. 正则化为什么可以避免过拟合？
正规化是防止过拟合的一种重要技巧。正则化通过降低模型的复杂性， 达到避免过拟合的问题。

范数总结/损失总结
[1](https://zhuanlan.zhihu.com/p/129782115)
[2](https://blog.csdn.net/colourful_sky/article/details/80684875)

参加比赛学到的深度学习调参trick：
1：多类问题考虑到样本不平衡问题
trian test split时候采用各个类别内部按比例分割的思路（StratifiedShuffleSplit）
2:数据预处理，
2.1：清理重复数据，使用dHash：差异值哈希。精确度较高，且速度也非常快来判断，https://www.jianshu.com/p/193f0089b7a2
后面数据增广，测试数据增广方案差不多前提下，这一步数据清洗能够提高1-2个百分点，很重要！！！
2.2：数据增强不只是有faster rcnn一种截取方式，还有(FCIS) https://github.com/msracver/FCIS (CAM) http://cnnlocalization.csail.mit.edu/