---
title: React-Native学习记录（Text组件）
date: 2017-03-14 09:30:03
tags:
---
+ <!-- more -->

### Text组件介绍
- 在React Native用于显示文本的组件就是Text，与iOS中的UILabel类似，专门用来显示文字信息，除了基本的显示布局之外，还可以嵌套显示，设置样式，以及可以做事件处理。  

### Text组件的常用属性方法

- color : 字体颜色
  
```
color : 'blue'
```

- numberOfLines 设置文本的行数。如果文字内容超过行数，默认超出文本不显示

```
<Text style={styles.textStyle} numberOfLines={3}>我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本我是一个文本</Text>
```

- fontSize : 字体大小

```
fontSize:20
```


- fontFamily 字体名称

```
fontFamily:'Verdana-BoldItalic'
```


- fontStyle enum('normal', 'italic') 字体风格

```
fontStyle : 'italic'//斜体
```

- fontWeight 字体粗细权重("normal", 'bold', '100', '200', '300', '400', '500', '600', '700', '800', '900')

- textShadowOffset （width: number, height: number）设置阴影效果
- textShadowColor : 阴影效果颜色


```
textShadowOffset :{width : 3 , height : 3},
textShadowColor : 'black'
```

- textShadowRadius : 阴影圆角 (值越大阴影越模糊)

```
textShadowRadius : 10
```

- letterSpacing : 字符间距

```
letterSpacing : 5
```

- lineHeight : 行高

```
lineHeight : 30
```

- textAlign : 文本对齐方式('auto', 'left', 'right', 'center', 'justify')

```
textAlign : 'center'
```

- textDecorationLine : 横线位置('none', 'underline', 'line-through', 'underline line-through')

```
textDecorationLine : 'underline line-through'
```
- textDecorationStyle 线的样式 （'solid', 'double', 'dotted', 'dashed'

```
textDecorationLine : 'underline line-through'
```

- textDecorationColor 线的颜色 

```
textDecorationColor : 'red'
```

- writingDirection 文本方向 ("auto", 'ltr', 'rtl')

```
writingDirection : 'ltr'
```

- allowFontScaling 控制字体是否要根据iOS的文本大小辅助选项来进行缩放
```
<Text style={styles.textStyle} numberOfLines={3} allowFontScaling={true}>我是一个文</Text>
```
- adjustsFontSizeToFit 指定字体是否随着给定样式的限制而自动缩放

- minimumFontScale 当adjustsFontSizeToFit开启时，指定最小的缩放比（即不能低于这个值）。可设定的值为0.01 - 1.0

- suppressHighlighting 当为true时，如果文本被按下，则没有任何视觉效果。默认情况下，文本被按下时会有一个灰色的、椭圆形的高光

- selectable 决定用户是否可以长按选择文本，以便复制和粘贴

```
<Text style={styles.textStyle} numberOfLines={3} selectable={true}>我是一个文</Text>
```
- testID 用来在端到端测试中标记这个视图

- onPress 当文本发生点击的时候调用该方法

```
<Text style={styles.textStyle}  onPress={()=>{alert('0')}}>我是一个文</Text>
```
![文本点击](https://cl.ly/22171M3d0G0e/111.gif)

- onLongPress 当文本长按以后调用改方法（与onPress用法一致）

- onLayout 当挂载或者布局变化以后调用（参数为：{nativeEvent: {layout: {x, y, width, height}}}）(与onPress用法一致)

### Text组件的嵌套使用

- 视图部分

```
render() {
    return (
      <View style={styles.container}>

        <Text style={styles.firstTextStyle} onPress={()=>{alert('点击第一段文字')}} suppressHighlighting={true}>
            第一段文字

          <Text style={styles.secondTextStyle} onPress={()=>{alert('点击第二段文字')}} suppressHighlighting={false}>
            第二段文字
          </Text>

        </Text>
      </View>
    );
  }
```
- 样式部分

```
firstTextStyle:{
    fontSize:20,
    backgroundColor : 'purple',
    width :300,
    height :30,
    color: 'black',

  },
  secondTextStyle:{
    color: 'red',
  },
```
![嵌套使用](https://cl.ly/3V2R1517462D/onPress.gif)

### Text组件中样式继承
- 在 React Native 中是没有样式继承这种说法的，但对于 Text 元素里边的 Text 元素，其实是可以继承的.
- 文字控制类的属性是多继承的，和CSS是一样的，而且会去自己最近的属性归自己所用。也就是属性覆盖。

