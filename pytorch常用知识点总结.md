# pytorch常用知识点总结
***
## 指定GPU运行指令
```language
# 使用终端命令行运行的 GPU 指定方式
CUDA_VISIBLE_DEVICES=1 python python_script.py
# 在 python 脚本中的 GPU 指定方式
import os
os.environ["CUDA_VISIBLE_DEVICES"] = "2"
```
