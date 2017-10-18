---
title: Trunk方式发布代码到Cocoapods
date: 2016-05-06 14:29:06
tags:
---

+ <!-- more -->


## 一、注册trunk

在注册trunk之前要确认当前的Cocoapods版本是否足够新。pod0.33及以上的版本才支持trunk.如果版本不对。打开终端更新cocoapods：


这里需要输入电脑密码<br>
`sudo gem install cocoapods`

更新结束后。可以注册trunk<br>

`pod trunk register xxx@xxx.com 'xxx' --verbose`

这里前面xxx@xxx.com是需要注册的邮箱，后面的xxx是用户名。执行完之后，邮箱会收到一封带有验证链接的邮件。照着邮件完成trunk的注册流程。

注册完成之后可以使用终端查询注册信息：

`pod trunk me`

成功的话可以看到自己的一些信息。如名字 邮箱 注册时间以及你自己的pods。

![Mou icon](https://s3.amazonaws.com/f.cl.ly/items/3u402F0M2t0P2O0S1p3g/Image%202016-05-23%20at%201.27.34%20%E4%B8%8B%E5%8D%88.png?v=859f30fd)

## 二、配置PodSpec
给代码添加podspec描述文件。然后将podspec文件通过trunk推送给Cocoapods。


* 1 在配置之前。需要先在github创建代码仓库（需要注意的是创建代码仓库的时候license类型选择MIT License
）
* 2 向本地git仓库之中添加后缀为.podspec文件(终端命令： vim xxx.podspec) 

<pre>
Pod::Spec.new do |s|
s.name             = "YQAlertView"
s.version          = "1.0.0"
s.summary          = "简单自定义AlertView"
s.homepage         = "https://github.com/yyqxiaoyin/YQAlertView"
s.license          = 'MIT'
s.author           = { "yyqxiaoyin" => "357491060@qq.com" }
s.source           = { :git => "https://github.com/yyqxiaoyin/YQAlertView.git", :tag => s.version.to_s }
s.platform     = :ios, '7.0'
s.requires_arc = true
s.source_files = 'YQAlertView/*'
end 
</pre> 
s.source_files
表示源文件的路径，注意这个路径是相对podspec文件而言的。

s.frameworks
需要用到的frameworks，不需要加.frameworks后缀。

也可以使用命令创建.podspec文件

`pod spec create YQAlertView`

也会创建名为YQAlertView.podspec文件。但是打开创建完的文件会发现里面我们不需要的东西太多。所以直接复制来的方便。


## 三、提交podspec文件到
* 1 提交之前。确保源码已经push到Github上。
* 2 确认github上已经有源码之后 给源码打上版本号


	` git tag '1.0.0' `
	
	`git push --tags`
* 3 确认以上两步都没问题的话。验证podspec文件的合法性：

	`pod lib lint`
	
验证完成如果没错误的话是这样：

![Mou icon](https://s3.amazonaws.com/f.cl.ly/items/2h3v1X302Y0Y3X0O1N0x/Image%202016-05-23%20at%202.09.45%20%E4%B8%8B%E5%8D%88.png?v=b06f66f6)

如果有错误。根据错误提示修改podspec文件

* 4 都没问题之后，就可以开始通过trunk上传podspec文件了。cd 到文件所在目录，执行:

`pod trunk push YQAlertView.podspec`

## 四、更新本地pod依赖

以上上传完了之后可以执行搜索命令查找刚刚上传到pod的代码：

`pod search YQAlertView`

如果搜索不到。更新本地依赖:

`pod setup`

再搜索一次。

![Mou icon](https://s3.amazonaws.com/f.cl.ly/items/2D0m0n1s3Q301v0A1S0w/Image%202016-05-23%20at%202.16.48%20%E4%B8%8B%E5%8D%88.png?v=1c3939de)

## 五、完成



