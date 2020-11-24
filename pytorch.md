# pytorch-dataset/dataloader总结
***
## torch.utils.data.Dataset
- 是一个抽象类，自定义数据集需要继承并实现两个成员方法
1. __getitem__()
- 作用是读取数据方式，示例：
```language
    def __getitem__(self, index):
        img_path, label = self.data[index].img_path, 	
        self.data[index].label
        img = Image.open(img_path)

        return img, label
```

2. __len__()
```language

```

 


