# real photo style transfer笔记
***
风格转换研究通常是进行某种艺术风格进行，实现真实的图像风格转换需要保证图像语义内容不改变，仅改变风格样式。
## 起源
- "Deep Photo Style Transfer" CVPR 2017
- [代码](https://github.com/luanfujun/deep-photo-styletransfer)
- 复现较为复杂，但是是本方向的起源文章，模型主要是实现了先用语义分割然后再风格迁移。这个模型可以用于多种情景，比如变换照片的时间，季节，天气，光线或者是art edit。
- 想要做photorealisitic的风格迁移难点在于既要保持图像原本的边缘结构不改变，又要改变局部的颜色和纹理，本文是第一个提出能解决这个问题并且有一定泛化能力的模型。



- 另一个难点在于解决“溢出”问题，这里点名批评MRF+CNN的方法，它的缺点在于只寻找style image中与输入的patch最相似的patch，然后迁移过来，这样就导致了有些style patches会被重复使用，而有些没有被用到，结果当然poorly了，而且找patches的过程也很迷，为啥不继续用gram矩阵呢，这冷漠的一耳刮子就扇了过去。本文用gram+提前语义分割，结果就很好嘛。