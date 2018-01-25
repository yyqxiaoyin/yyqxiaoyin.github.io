---
title: React-Native学习记录（Image组件）
date: 2017-03-16 9:44:11
tags:
---
+ <!-- more -->

### Image组件的常用属性方法

##### 属性方法:
- onLoad(function）:当图片加载成功后，回调该方法
 
- onLoadStart（function）:当图片开始加载的时候调用该方法
 
- onLoadEnd(function）:当图片加载失败回调该方法，不会管图片加载成功还是失败
 
- onLayout（function）:当 Image 布局发生变化会调用该方法，调用代码
 
- resizeMode:缩放比例，（包含可选参数'cover', 'contain', 'stretch'）,当该图片的尺寸超过布局的尺寸时，会根据设置 Mode 进行缩放或剪裁图片
 
- source{uri:string}:进行标记图片引用，该参数可以为一个网络 url地址 或者 一个本地路径

##### 样式属性:

- FlexBox：支持弹性盒子风格

- Transforms：支持属性动画

- backgroundcolor：背景颜色

- borderColor：边框颜色

- borderWidth：边框宽度

- borderRadius：边框圆角

- overflow：设置图片尺寸超过容器可以设置显示或隐藏('visible', 'hidden')

- tintColor：颜色设置

- opacity：设置透明度（取值范围0.0（全透明）~ 1.0（不透明））


### Text组件的嵌套使用

- 不设置尺寸的情况下，默认会根据图片资源的大小来展示图片

- 可以通过设置尺寸或者改变 Image 的填充模式来改变所展示的图片样式


```
<Image source={require('./img/icon.jpg')} style={styles.imgStyle}></Image>
```
- 加载APP中的图片资源: 把图片放到 images.xcassets 中，这样在编译链接完成后，会将里面的图片统一打包以供使用
- 加载来自网络的图片



```
<Image source={{uri:'https://xxx.jpg'}} style={styles.imgStyle}></Image>
```
### Image组件的填充模式
- cover( 默认)：图片居中显示且不拉伸图片，超出的部分剪裁掉
- contain：容器完全容纳图片，图片等比例进行拉伸
- stretch：图片被拉伸至与容器大小一致，可能会发生变形

### 往Image组件上添加一个Text组件

```
<Image source={{uri:'https://xxx.jpg'}} style={styles.imgStyle}>
    <Text style={{marginTop:100}}>覆盖在图片上的文字</Text>
      </Image>

```

