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
- 其一共干了两件事: 
1. 定义了一堆成员变量, 到时候赋给DataLoaderIter
2. 然后有一个__iter__() 函数, 把自己 "装进" DataLoaderIter 里面.
## torch.utils.data.dataloader.DataLoaderIter
- 作用是封装dataloader用于遍历
```language
class CustomDataset(Dataset):
   # 自定义自己的dataset

dataset = CustomDataset()
dataloader = Dataloader(dataset, ...)

for data in dataloader:
   # training...
```
在for 循环里, 总共有三点操作:

1. 调用了dataloader 的__iter__() 方法, 产生了一个DataLoaderIter
2. 反复调用DataLoaderIter 的__next__()来得到batch, 具体操作就是, 多次调用dataset的__getitem__()方法 (如果num_worker>0就多线程调用), 然后用collate_fn来把它们打包成batch. 中间还会涉及到shuffle , 以及sample 的方法等, 这里就不多说了.
3. 当数据读完后, __next__()抛出一个StopIteration异常, for循环结束, dataloader 失效.

 


