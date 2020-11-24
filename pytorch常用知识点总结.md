# pytorch常用知识点总结
***
## 指定GPU运行指令
```language
# 使用终端命令行运行的 GPU 指定方式
CUDA_VISIBLE_DEVICES=1 python python_script.py
# 在 python 脚本中的 GPU 指定方式
import os
os.environ["CUDA_VISIBLE_DEVICES"] = "2"
# set_device不建议使用
torch.cuda.set_device(id)
```
## os.mkdir()和os.makedirs()区别
- mkdir只创建最后一级目录，mkdirs创建递归目录

## Matplotlib中plt.rcParams用法（设置图像细节）
```language
import matplotlib.pyplot as plt
plt.rcParams['font.sans-serif'] = ['SimHei']  # 用来正常显示中文标签
plt.rcParams['axes.unicode_minus'] = False  # 用来正常显示负号
```
## @staticmethod和@classmethod的作用与区别
- 一般来说，要使用类的方法，需先实例化对象再调用其方法
- 