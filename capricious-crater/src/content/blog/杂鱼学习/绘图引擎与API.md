---
title: ’图形引擎与API'
description: '计算机图形'
pubDate: 'Mar 31 2024'
heroImage: '/placeholder-hero.jpg'
---

>大多数游戏引擎都对这些图形API封装成统一的接口，可以在不同的平台上切换来追求更好的图形性能，我们一般称这套接口为 **RHI** （Rendering Hardware Interface）



2D图形API:

- Skia Google在用

- GDI,GDI+  Windows

- Direct2D Windows

- Cairo

  

3D图形API：

- DX11、[DX12](https://www.nvidia.com/en-sg/geforce/technologies/dx12/)：[微软](https://zh.wikipedia.org/wiki/微軟)公司在[Windows](https://zh.wikipedia.org/wiki/Microsoft_Windows)系统上所开发的3D图形编程接口
- [OpenGL](https://www.opengl.org/)：OpenGL是一套跨语言、跨平台的API，它的实现存在于Windows、部分UNIX和Mac OS，这些实现一般由显卡厂商提供，而且非常依赖于该厂商提供的硬件。
- [Vulkan](https://www.vulkan.org/)：下一代的OpenGL，相比之下，Vulkan更接近底层，并且能很好地分配CPU核心来执行并行任务
- [Metal](https://developer.apple.com/metal/)：Metal API 由苹果公司提供，它旨在为[iOS](https://en.wikipedia.org/wiki/IOS)、[iPadOS](https://en.wikipedia.org/wiki/IPadOS)、[macOS](https://en.wikipedia.org/wiki/MacOS)和[tvOS](https://en.wikipedia.org/wiki/TvOS)上的应用程序提供对GPU硬件的低级访问来提高性能，它与Vulkan、DX12都属于低级别的API

所以基本从OpenGL的接口入手编程学习了.

[OpenGL之gult/freeglut/glew/glfw/glad的联系与区别_opengl中的glfw,glew,stb,glm是干嘛呢的-CSDN博客](https://blog.csdn.net/qq_38446366/article/details/115328051)

其他库,不直接从OpenGL学习,而是学一些更加全面的东西.

### SDL

SDL是一个跨平台的多媒体开发库，用于游戏开发和其他多媒体应用。以下是SDL的特点：

2D图形渲染： SDL提供了2D图形渲染的功能，虽然不如SFML那样高级，但仍然足够满足一般的2D游戏需求。
音频： SDL支持音频播放，但相较于SFML而言，其音频功能较为基础。
窗口和事件处理： 提供了创建窗口、处理鼠标、键盘事件的功能。
低级硬件访问： SDL也提供了对硬件的低级访问，使得开发者可以更灵活地操作硬件。

### SFML

SFML是一个现代、面向对象的多媒体库，专注于2D游戏开发和多媒体应用程序。以下是SFML的特点：

2D图形渲染： SFML提供了简单易用的2D图形渲染接口，使得创建2D游戏非常容易。
音频： SFML支持音频播放和音频捕获功能，可以用来添加音乐、音效等。
窗口和事件处理： 提供了创建窗口、处理鼠标、键盘事件的功能。
网络： SFML包含网络模块，允许游戏之间进行网络通信。













##  参考资料

1. [主页 - LearnOpenGL CN (learnopengl-cn.github.io)](https://learnopengl-cn.github.io/)英文[LearnOpenGL - OpenGL](https://learnopengl.com/Getting-started/OpenGL)
2. [Tutorial 01 - Create a window (ogldev.org)](https://ogldev.org/www/tutorial01/tutorial01.html)
3. [Home (opengl-tutorial.org)](https://www.opengl-tutorial.org//)
4. [Modern Graphics Engine Guide (italink.github.io)](https://italink.github.io/ModernGraphicsEngineGuide/01-GraphicsAPI/0.概述/#api_1)
5. [【漫谈】关于图形引擎的一些看法 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/639795542)
6. [The OpenGL Programming Guide (opengl-redbook.com)](http://www.opengl-redbook.com/)
7. [OpenGL超级宝典（第7版） (豆瓣) (douban.com)](https://book.douban.com/subject/35221845/)
8. OpenGL 4.0 Shading Language Cookbook》
9. 《OpenGL Shading Language》

