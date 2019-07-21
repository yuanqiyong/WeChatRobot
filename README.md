[TOC]

## 前言

最近一直都在研究微信逆向相关的东西，奈何目前所有相关的的接口和成品都在收费，所以就打算自己写一个，然后开源。

## 实现功能

![WeChatHelper](assets/WeChatHelper.png)

## 项目介绍

![1563679851680](assets/1563679851680.png)

![1563679859287](assets/1563679859287.png)

项目分为两个端，WeChatRobot和WeChatHelper。WeChatRobot作为客户端负责和服务端进行通信，将服务端传回的数据显示到界面。WeChatHelper作为服务端，注入到微信进程，进行取数据和HOOK的相关操作，并且将取回的数据发回给客户端。

客户端和服务端之间采用WM_COPYDATA的方式进行进程通讯，互相传输数据

## 效果演示

下面演示部分效果

### 初始化

![1563680047243](assets/1563680047243.png)

将WeChatRobot.exe和WeChatHelper.dll放在同一个目录下，先打开微信，再打开exe

![1563680573456](assets/1563680573456.png)

### 截取二维码

![1563680585192](assets/1563680585192.png)

点击显示二维码 微信会自动跳转并截取二维码显示到客户端，再次点击可以刷新二维码

### 检测微信登陆状态&显示所有联系人

![显示联系人](assets/显示联系人.gif)

这里由于WM_COPYDATA通信状态下是阻塞的原因 所以联系人多的话可能会有些卡顿

### 发送文本 图片 和文件消息 

![发送文本 图片 文件消息](assets/发送文本 图片 文件消息.gif)

### 添加&删除好友

![添加和删除好友](assets/添加和删除好友.gif)

### 接收并显示所有类型消息

![1563686929418](assets/1563686929418.png)

### 无限多开

![1563687391099](assets/1563687391099.png)

### 解密数据库

![解密数据库](assets/解密数据库.gif)

### 自动聊天

![自动聊天](assets/自动聊天.gif)

### 自动收款

![自动收款](assets/自动收款.gif)

### 自动提取微信表情

微信的表情加密存放在下面的目录

``C:\Users\GuiShou\Documents\WeChat Files\crt873217126\FileStorage\CustomEmotion``

![1563686532775](assets/1563686532775.png)

这个功能会将所有的未加密的表情存放到Temp目录下的WeChatExpressions文件夹里

还有很多效果，就不一一录制演示Gif了

## 成品和编译环境

![1563688306832](assets/1563688306832.png)

需要同时包含这几个文件才能运行，没有静态编译 可能需要VS环境。 目前只支持微信2.6.8.52版本。项目使用VS2017编译

## 技术细节

PCXX逆向：使用CE+OD查找个人数据：https://blog.csdn.net/qq_38474570/article/details/92571302

PCXX逆向：使用HOOK拦截二维码：https://blog.csdn.net/qq_38474570/article/details/92798577

PCXX逆向：发送与接收消息的分析与代码实现：https://blog.csdn.net/qq_38474570/article/details/93339861

PCXX逆向：使用HOOK获取好友列表和群列表：https://blog.csdn.net/qq_38474570/article/details/95889507

PC微信逆向：两种姿势教你解密数据库文件：https://blog.csdn.net/qq_38474570/article/details/96606530

## 声明

**本项目仅供技术研究，请勿用于任何商业用途，请勿用于非法用途，如有任何人凭此做何非法事情，均于作者无关，特此声明。**

## 项目地址

https://github.com/TonyChen56/WeChatRobot

开源不易，求个star