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
- 作用是返回数据集的长度，示例：
```language
    def __len__(self):
        return len(self.data)
```
## torch.utils.data.DataLoader
- 类的定义：
- class torch.utils.data.DataLoader(dataset, batch_size=1, shuffle=False, sampler=None, batch_sampler=None, num_workers=0, collate_fn=<function default_collate>, pin_memory=False, drop_last=False)
- 
 


