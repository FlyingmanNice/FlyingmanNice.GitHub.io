
---
title: UE5简易建立MultiPlayer流程
categories: 
- Test
tags:
- Test1
- Test2
---
## 配置UE5

以Steam为例

### 1. Enable Online Subsystem Steam 插件
![](/pic/UE5简易建立MultiPlayer流程/1.png)
### 2. 在.Build.cs文件Enable相关的Module
![](/pic/UE5简易建立MultiPlayer流程/2.png)
PS:目前5.2需要关闭Live-Coding才能在Rider直接编译

### 3. 为Steam配置项目
打开DefaultEngine.ini
![](/pic/UE5简易建立MultiPlayer流程/3.png)

具体配置看:[ Online Subsystem Steam](https://docs.unrealengine.com/5.2/en-US/online-subsystem-steam-interface-in-unreal-engine/)
![](//pic/UE5简易建立MultiPlayer流程/4.png)
### 4.重新生成项目
#### a. 关闭引擎
#### b. 删除生成文件
![](/pic/UE5简易建立MultiPlayer流程/5.png)
#### c. 生成项目
![](/pic/UE5简易建立MultiPlayer流程/6.png)
## 具体流程
![](/pic/UE5简易建立MultiPlayer流程/7.png)

## Host
### 获取OnlineSessionInterface
取得OnlineSubsystem里Session的接口类，为后续Session的开发做准备：
![](/pic/UE5简易建立MultiPlayer流程/8.jpg)
![](/pic/UE5简易建立MultiPlayer流程/9.png)
### 创建Session，并作为Listen Server进入Lobby关卡
添加OnCreateSession的Delegate，还有CreateSession和OnCreateSession方法
![](/pic/UE5简易建立MultiPlayer流程/10.png)
用OnlineSessionInterface提供的方法来创建Session
![](/pic/UE5简易建立MultiPlayer流程/11.png)
绑定创建Session的回调
![](/pic/UE5简易建立MultiPlayer流程/12.png)
回调成功则作为Listen Server进入Lobby关卡
![](/pic/UE5简易建立MultiPlayer流程/13.png)
