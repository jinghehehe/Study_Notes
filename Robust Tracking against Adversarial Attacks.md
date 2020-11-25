# Robust Tracking against Adversarial Attacks 论文点摘录
***
- 本文发表在ECCV2020，是针对于单目标跟踪得攻击防御算法，代码部分开源，[代码链接](https://github.com/joshuajss/RTAA)。
- 本文在逐帧估计的跟踪上，考虑时间运动，生成轻量级扰动。一方面，将时间扰动作为对抗样本添加到原始视频序列中，从而大大降低了跟踪性能。 另一方面，从输入序列中顺序估计扰动，并学习消除其影响以恢复性能。