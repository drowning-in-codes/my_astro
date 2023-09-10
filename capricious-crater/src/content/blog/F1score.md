---
title: 'F1-score'
description: '机器学习'
pubDate: 'Sep 8 2023'
heroImage: '/placeholder-hero.jpg'
---
众所周知,F1-score是通过混淆矩阵算出来的

![image-20230902095411905](https://s2.loli.net/2023/09/02/uaCN1QkZrLVjElP.png)

<img src="https://math.jianshu.com/math?formula=\text {precision} %3D\frac{\text {TP}}{\text {TP}%2B\text {FP}}\\ \text {recall} %3D\frac{\text {TP}}{\text {TP}%2B\text {FN}}" alt="\text {precision} =\frac{\text {TP}}{\text {TP}+\text {FP}}\\ \text {recall} =\frac{\text {TP}}{\text {TP}+\text {FN}}"  />

![](https://math.jianshu.com/math?formula=\text{F1 score}%3D\frac{2}{\frac{1}{\text{precsion}}%2B\frac{1}{\text{recall}}}%3D \frac{2*\text{precsion}*\text{recall}}{\text{precsion}%2B\text{recall}})

TP代表预测正类，预测正确,FN代表预测负类,但是预测错误了.

这样就能计算某个类别的F1-score了.但是其实F1-score还可以使用TP,FN等定义来计算,这两个公式是一样的.

![image-20230902120824729](https://s2.loli.net/2023/09/02/lIw5KqrNxjtDEXH.png)

>F1分数是一个按类计算的指标，这意味着如果你想计算一个包含多个类的数据集的总体F1分数，你需要以某种方式进行聚合。微观和宏观F1分数是进行这种聚合的两种方式。

当计算多类(这里包括两类)的F1-score时一般又分为微F1和宏F1,也就是Micro和Macro.

## Macro F1

| Class   | TP     | FP     | FN     | F1 score |
| :------ | :----- | :----- | :----- | :------- |
| 0       | 10     | 2      | 3      | 0.8      |
| 1       | 20     | 10     | 12     | 0.6      |
| 2       | 5      | 1      | 1      | 0.8      |
| **Sum** | **35** | **13** | **16** |          |

比如上面的三类,计算得到分别的F1,然后多类的F1-score的如果使用macro方式计算直接计算平均值即可。

对于class 0,首先准确率为10/12=0.83,查全率为10/13=0.769,则F1为1.27654/1.699=0.798,取0.8,同理算出所有类别的F1.则Macro F1为**`Macro F1 score = (0.8+0.6+0.8)/3 = 0.73`**

![image-20230902120516225](https://s2.loli.net/2023/09/02/cx3lg5VriHZIzKW.png)

## Micro F1

> Micro F1分数是使用真阳性（TP）、假阳性（FP）和假阴性（FN）的总数来计算，而不是针对每个类别单独计算。

| Class   | TP     | FP     | FN     | F1 score |
| :------ | :----- | :----- | :----- | :------- |
| 0       | 10     | 2      | 3      | 0.8      |
| 1       | 20     | 10     | 12     | 0.6      |
| 2       | 5      | 1      | 1      | 0.8      |
| **Sum** | **35** | **13** | **16** |          |

类似上面的表格,计算Micro F1的话,直接套公式,**`Micro F1 score = 35 / (35 + 0.5 \* (13 + 16)) = 0.71`**,相当于把三类的数据当作一样的的了



## FAQ

1. ### 对于不平衡的数据集，Micro还是Macro F1得分更好

micro F1-score 在不平衡数据集上的表现比macro F1差。这是因为micro F1对**每个观测值(样本)**都具有同等的重要性，而macro F1是对**每个类别**都具有同等重要性。

也就是当某个类别中数据特别多,其他类别数据比较少时,Micro F1会更多考虑数据特别多的类.最终的分数掩盖了少数的表现，放大了大多数的表现。

2. ### 为什么scikit学习分类报告中没有Micro平均值

当目标是单标签分类时，微观平均F1分数在分类报告中显示为accuracy。

这样做是因为在这种情况下，微观平均F1分数返回的值与accuracy相同

### 3.micro 和macro F1 有什么区别

micro 和macro F1分数之间的关键区别在于它们在不平衡数据集上的行为。当类不平衡时，micro F1分数通常不会返回模型性能的客观衡量标准，而macro F1分数可以这样做。

## 总结

如果你有一个不平衡的数据集，那么你应该使用macroF1分数，因为即使类是偏斜的，这仍然会反映真实的模型性能。然而，如果你有一个平衡的数据集，那么可以考虑microF1分数，特别是如果与最终用户交流结果很重要的话。



## 参考资料

1. [Micro vs Macro F1 score, what’s the difference? (stephenallwright.com)](https://stephenallwright.com/micro-vs-macro-f1-score/#:~:text=The key difference between micro and macro F1,Another difference between the two metrics is interpretation.)