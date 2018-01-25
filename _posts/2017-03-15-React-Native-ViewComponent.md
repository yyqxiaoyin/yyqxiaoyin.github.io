---
title: React-Native学习记录（View组件）
date: 2017-06-23 11:02:22
tags:
---
+ <!-- more -->

### View组件介绍
- React Native 组件 View,其作用等同于iOS中的 UIView,它是所有组件的父组件，也可以说所有组件继承了它的所有属性

### View组件的常用属性方法

- Flexbox : 弹性布局

- Transforms：动画属性

- backfaceVisibility('visible', 'hidden')：定义界面翻转的时候是否可见


- backgroundColor：背景颜色

```
backgroundColor:'red'
```


- borderBottomColor：底部边框颜色

```
// 底部边框宽度
    borderBottomWidth:3,
    // 底部边框颜色
    borderBottomColor:'red'
```

- borderBottomLeftRadius：底部左边边框圆角

```
borderBottomLeftRadius:10
```

- borderBottomRightRadius：底部右边边框圆角
```
borderBottomRightRadius:10
```
- borderBottomWidth：底部边框宽度

```
borderBottomWidth:5
```

- borderColor：边框颜色

```
// 全体边框宽度
    borderWidth:5,
    // 全体边框颜色
    borderColor:'yellow'
```

- borderLeftColor：左边框颜色

```
// 左边边框颜色
    borderLeftColor:'black'
```

- borderLeftWidth：左边边框宽度

```
borderLeftWidth:10
```

- borderRadius：边框圆角

```
// 全体边框宽度
    borderWidth:5,
    // 全体边框颜色
    borderColor:'black',
    // 全体边框圆角
    borderRadius:3
```

- borderRightColor：右边边框颜色

```
// 右边框颜色
    borderRightColor:'yellow'
```
- borderRightWidth：右边边框宽度

```
// 右边框宽度
    borderRightWidth:10
```

- borderStyle('solid', 'dotted', 'dashed')：边框风格

```
// 边框风格
    borderStyle:'solid'
```

- borderTopColor：顶部边框颜色（参考上面）

- borderTopWidth：顶部边框宽度（参考上面）

- borderTopLeftRadius：顶部左边圆角（参考上面）

- borderTopRightRadius：顶部右边圆角（参考上面）

- borderWidth：边框宽度
- opacity：设置透明度，取值从 0~1
```
opacity:0.5
```
- overflow('visible', 'hidden')：设置内容超出容器部分是否显示
- elevation：高度，设置Z轴，可产生立体效果

### Text组件的嵌套使用

- 视图部分

```
var test = React.createClass({
        render() {
            return (
                <View style={styles.container}>
                    <View style={styles.viewStyle}>

                    </View>
                </View>
            );
        }
    });
```
- 样式部分

```
var styles = StyleSheet.create({
        container: {
            flex: 1,
            justifyContent: 'center',
            alignItems: 'center',
            backgroundColor: '#F5FCFF',
        },

        viewStyle: {
            // 尺寸
            width:300,
            height:100,
            // 背景颜色
            backgroundColor:'red',
            // 边框宽度
            borderWidth:1,
            // 边框颜色
            borderColor:'black'
        }

    });
```

