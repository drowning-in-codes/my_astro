---
title: 'GPU不完全测评'
description: 'GPU不完全测评'
pubDate: 'Oct 26 2023'
heroImage: '/placeholder-hero.jpg'
---

由于本人没有合适的GPU服务器训练模型(没钱买服务器),只能在网上租了.

我的评价标准:

1. GPU要求,这个要看具体论文或者情况.需要用什么GPU就用什么的,否则太好的价格承担不起.
2. 价格便宜
3. 需要有及时回复问题的客服
4. 最好是国外服务器(或者能方便连外网,不然一些数据集什么的不好获取)
5. 自带的镜像版本要多,一定程度的定制化,不然一个python版本或者pytorch的版本跑不了
6. 有单独的存储服务,而不是每次都去服务器上运行下载命令.存储空间要大,因为一般数据集可能很大(一两百多个G)
7. 加分点:能直接使用网盘,这样就不用每次去下载数据集了.

## 国内

国内我就只推荐autodl.

### AutoDL

4090和V100都有,介个不贵,关键是支持阿里和百度网盘传数据.

![image-20231024225120243](https://i.imgur.com/hnAlSJC.png)

**实例连续关机15天会释放实例，实例释放会导致数据清空且不可恢复，释放前实例在数据在。**也支持所谓学术资源加速,在访问github和huggingface的之后能正常访问.

此外还有所谓省钱绝招[AutoDL帮助文档](https://www.autodl.com/docs/save_money/)

1. 有无卡模式用于`编写/调试代码、上传下载数据到实例、给他人做代码展示等不需要GPU卡场景时`,这个时候价格0.1元/时,这个很人性化.
2. 随时升降配置`开始仅需要1块GPU进行代码调试和性能验证，但是调试完成后为了加速训练需要使用多卡并行`
3. 不确定自己的代码需要执行多久结束，希望执行完成后立马关机。这类场景可以通过`shutdown` 



> AutoDL可以通过ssh和jupyter
>
> 在代码最后加上os.system('shutdown'),然后使用nohup等命令挂在后台运行，代码运行完就会自动关机停止计费。



## 国外

国外的很多都需要绑定国外信用卡,很多都不支持国内支付宝.

### Vast.ai

![image-20231024225911924](https://i.imgur.com/Gd5jGvg.png)

主打的便宜,我一般用4090人民币2元多一小时,有的服务器是支持jupyter notebook有的只能使用ssh连接,这需要自己去修改一下配置

![image-20231025123946278](https://i.imgur.com/h4ZwPrc.png)

vast.ai也支持类似autodl无卡机制,可以先把机子stop了(数据会保留,但后面不一定能用上该机器了,如果用不上可以拷贝数据到其他机子上). 

### paperspace

8美元1个月,感觉还行,有免费额度(但不一定能抢得到)

存储空间支持的云服务商包括DO,亚马逊,还不包括谷歌云盘

![image-20231025125027673](https://i.imgur.com/ldOrarY.png)



### Lambda

可以租赁的GPU类型特别多,价格一般

![image-20231025124511039](https://i.imgur.com/X9euOmX.png)

界面不错,感觉应该是一众网站中的质量较高的GPU服务器商了.

### JarvisLabs

![image-20231024230630551](https://i.imgur.com/E3S2UFE.png)

我自己没用过,但是看周围评价说是不错的,而且对AI绘画和llm chat也有支持

![image-20231025133202526](https://i.imgur.com/zuylJzw.png)



如果你对之前的AI绘图感兴趣,我推荐RunDiffusion](https://app.rundiffusion.com/)和[Think Diffusion: Stable Diffusion in the Cloud](https://www.thinkdiffusion.com/)



除此之外还有国内外大厂的,比如国外微软谷歌亚马逊,国内腾讯百度阿里,这种租赁GPU服务器的都有,质量是肯定可以保障的,不过价格啥的应该要贵一点,而且一些操作比较繁琐(我用过微软和亚马逊的服务器(学生服务),整个价格介绍啥的都很多、繁琐)



### 目前setup

先用google colab测试,如果机子不太行经常断连,尝试上autodl或者vast.ai

## 存在问题

主要是网络问题以及存储数据问题,比如我想下载一共200G左右在谷歌云盘的数据集到服务器.

如果使用国内的服务器,这不太行,本身无法访问谷歌,如果自己搭建代理可能更麻烦

如果用国外服务器,我尝试过vast.ai的谷歌云盘功能,很多时候不太行.只能自己在服务器上使用命令行下载,这样挂着下载又要花一笔钱.实用工具gdown,gdrive等,不过gdown下载文件还有限制....

或者自己下载到本地再传上去,这是最简单也最笨的方法.

目前参照了[如何下载Google Drive中的超大型文件 - Max1z - 博客园 (cnblogs.com)](https://www.cnblogs.com/max1z/p/15982508.html)的方案,话说直接使用vast.ai的服务器就行了,其他服务器就算了,放在那下载数据花钱太多.

```bash
curl -H "Authorization: Bearer YOUR_ACCESS_TOKEN" https://www.googleapis.com/drive/v3/files/YOUR_FILE?alt=media -o OUTPUT_FILE
sudo ufw app list
sudo ufw allow 'Nginx Full'
```

