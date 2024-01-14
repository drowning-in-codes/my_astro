---
title: '论文Idea'
description: '记录一下看论文或者写论文时的idea'
pubDate: 'Jan 07 2024'
heroImage: '/placeholder-hero.jpg'
---

平时写论文的时候有些想法把这些记录下来.
学习Pytorh和深度学习资料.目前找到的比较好的

- ZeroToMastery的**pytorch学习资料**,有对应的题和答案,质量不错.
- **李宏毅的深度学习课程**(建议至少从2021年的看),也有每章对应作业.
- 微软的**深度学习以及生成式人工智能课程**,高质量,前沿.
- **fast.ai**的课程[Practical Deep Learning for Coders - Practical Deep Learning (fast.ai)](https://course.fast.ai/).内容比较多,关于diffusion models介绍也多.
- 还有**Deep Leaning**上吴恩达的一些short course,比较实用和前沿(比如Gradio和wandb).

现在生成式人工智能课程内容比较多,llm的内容也比较多,但大多数人没那个训练资源,成本不小.



## OPV2V

范围感知CNN,损失函数更改,多尺度attention fusion.

现实世界存在的问题:1)单车目标检测存在的检测问题

2)通信时周围车定位问题

3)通信时带宽问题

三个主要问题**通信延迟,数据传输可靠性,定位错误**

 通过特殊模块(或称为辅助模块)处理通信和点云(特征)互补信息提升可靠性.模块轻量,传递的特征数据少(使用注意力机制).

**低延迟和高可靠性是V2V通信面临的两个常见挑战。例如，在碰撞前感知场景中，最大延迟仅为 20 ms，数据传输可靠性必须大于 99%**

发射机和接收机之间的障碍物（车辆、建筑物等）会导致信号功率波动，从而造成丢包.



 

- 通过特殊模块(或称为辅助模块)处理通信和点云(特征),利用互补信息提升可靠性.融合模块轻量,传递的特征数据少(使用注意力机制).
- 强调在真实环境(存在延迟或通信错误情况下)
- 提出特征融合模块?
- 传递的特征根据与ego车辆的距离加权(注意力)?





根据周围车距离进行注意力特征加权,提出去噪模块(optional)作为通信过程中对数据产生的可能噪声的移除.

multiscale range-aware attention

利用较新又好用的attention或者transformer机制进行融合

调研swin-transformer

cnn-transformer?

理想达到的效果,在真实环境(或符合真实环境)下表现优于其他模型(数据集OPV2V,V2V4REAL,V2XSet)

agent置信度?agent confidence?



Range-aware配合单车 localization error减小下提升协同感知能力.





new: Target-aware fuse,设置融合函数更新融合模块权重



点云 需要使用对近处和远处物体有不同探测能力的检测网络 centerpoint raanet

自动驾驶

目标检测 感知

协同感知















