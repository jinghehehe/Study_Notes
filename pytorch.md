# pytorch-dataset/dataloader总结
***
## torch.utils.data.Dataset
- 是一个抽象类，自定义数据集需要继承并实现两个成员方法
1. __getitem__()