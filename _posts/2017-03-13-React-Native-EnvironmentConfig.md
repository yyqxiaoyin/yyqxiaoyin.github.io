---
title: React-Native学习记录（配置环境）

date: 2017-03-13 14:29:06
tags:
---

+ <!-- more -->

##### 一、环境需求
###### 1.1安装Homebrew

```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
    
###### 1.2安装npm和Node.js

```
brew install node
```
    
##### 1.3安装WatchMan
> WatchMan是由Facebook提供的监视文件系统变更的工具。安装此工具可以提高开发时的性能（packager可以快速捕捉文件的变化从而实现实时刷新）。

```
brew install watchMan
```

##### 二、React Native安装
###### 2.1 Yarn、React Native的命令行工具(react-native-cli)
> Yarn能加速node木块的下载。react-native-cli 用于执行创建、初始化、更新项目、运行打包服务等任务

```
npm install -g yarn react-native-cli
```

##### 三、Android开发环境需求

###### 3.1 安装Genymotion模拟器
> 安装最新版的JDK  Android studio

> Genymotion是一个第三方模拟器，它比Google官方的模拟器更易设置且性能更好。但是，它只针对个人用户免费。

-  下载并安装VirtualBox  下载地址：https://pan.baidu.com/s/1geNnIJT
-  下载并安装Genymotion  下载地址：https://www.genymotion.com/
-  打开Genymotion Add一个自己想要的模拟器(需要登录Genymotion) 选完之后自己下载，但速度奇慢无比且经常断线。可在 /Users/用户名/.Genymobile 目录下找到一个genymotion.log文件。打开genymotion文件并搜索Downloading 找到刚刚选中模拟器的下载地址下载


  ![模拟器下载地址](https://cl.ly/0g412N183J0R/Image%202017-06-22%20at%202.41.39%20%E4%B8%8B%E5%8D%88.png)

- 下载完成后打开VirtualBox command+i 添加上一步下载的模拟器(后缀名为.ova)

###### 3.2 Gradle Daemon
> 开启Gradle Daemon可以极大地提升java代码的增量编译速度。

```
touch ~/.gradle/gradle.properties && echo "org.gradle.daemon=true" >> ~/.gradle/gradle.properties
```

##### 四、 创建React Native 项目
###### 4.1 切换npm仓库源为国内镜像(已经翻墙的请无视)
```
npm config set registry https://registry.npm.taobao.org
```
```
npm config set disturl https://npm.taobao.org/dist
```
###### 4.2 执行命令，生成一个React-Native工程

```
react-native init 项目名称

```
指定react-native 跟 react版本创建项目：
```
react-native init 项目名 --version react-native@0.44.3 react@16.0.0-alpha.6
```

> 过程中会从npm源下载必要的组件，需要保持网络畅通

创建成功截图


![创建项目成功截图](https://cl.ly/1d0H0u0A3t1P/Image%202017-06-22%20at%202.56.27%20%E4%B8%8B%E5%8D%88.png)

如果中途出现如下图的警告


![警告](https://cl.ly/1S080J36361S/Image%202017-06-22%20at%202.58.03%20%E4%B8%8B%E5%8D%88.png)


可能会出现编译失败的情况 

解决方法：

指定react-native版本跟react版本重新创建项目

```
react-native init 项目名 --version react-native@0.44.3 react@16.0.0-alpha.6
```
##### 五、运行工程
> 不管是iOS还是安卓，在开发调试阶段，都需要在 Mac 上启动一个 HTTP 服务，称为Debug Server，默认运行在 8081 端口，APP 通 Debug Server 加载 js。不要关掉。

###### 5.1 iOS打开项目成功截图：

![iOS运行项目成功](https://cl.ly/452f0K2T301R/Image%202017-06-22%20at%203.09.35%20%E4%B8%8B%E5%8D%88.png)

###### 5.2安卓运行项目

1. 打开Genymotion选择一个模拟器运行
2. 打开Android studio 打开项目(选择项目目录下的android目录)
3. control + r 运行安卓app 选中下载好的模拟器(Genymotion打开模拟器后Android studio自动识别)  
  
选择安卓模拟器截图：  

![选择安卓模拟器](https://cl.ly/2U2a0m0T1e3t/Image%202017-06-22%20at%203.17.49%20%E4%B8%8B%E5%8D%88.png)

安卓运行成功截图：  
![安卓运行成功截图](https://cl.ly/1T450O293D3L/Image%202017-06-22%20at%203.21.25%20%E4%B8%8B%E5%8D%88.png)  

##### 六、管理React Native库的版本
###### 6.1 查看本地React Native库版本
```
react-native --version

```
###### 6.2 更新本地的React Native的版本
```
npm update -g react-native-cli
```
###### 6.3 切换React Native 项目中的react-native库版本 

```
npm install --save react-native@版本号 react@版本号
```

###### 6.4 查看react-native版本信息
```
npm info react-native
```

##### 七、WebStom设置React Native代码提示
###### 7.1 从gitHub上下载xml插件
```
git clone https://github.com/virtoolswebplayer/ReactNative-LiveTemplate  
```
###### 安装方法
方法1
- 将ReactNative.xml文件复制到/Users/用户名/Library/Preferences/WebStorm版本/templates 然后重启WebStrom  

方法2
- 打开WebStrom File->Import setting->导入ReactNative.jar


