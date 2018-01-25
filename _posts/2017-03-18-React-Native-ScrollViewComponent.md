---
title: React-Native学习记录（ScrollView组件）
date: 2017-03-18 15:32:13
tags:
---
+ <!-- more -->

### ScrollView组件介绍
- React Native中的 ScrollView 的组件除了包装滚动平台，还集成了触摸锁定的 响应者 系统，使用的时候有几点需要注意

- ScrollView 必须有一个确定的高度才能正常工作,对于 ScrollView 来说，它就是将一些不确定高度的子组件装进确定高度的容器

- 初始化的2中方式
    * 不要给 ScrollView 中不要加 [flex:1]

    * 直接给该 ScrollView 设置高度（不建议），因为它会根据内部组件自动延伸自己的尺寸到合适的大小

- ScrollView 内部的其它响应者没办法阻止 ScrollView 本身成为响应者（也就是说，ScrollView 响应的优先级比内部组件高，且内部组件没办法改变优先级）
- 创建基本的 ScrollView
    * 视图部分

    ```
    var CustomScrollView = React.createClass({
        render(){
            return(
                <ScrollView style={styles.mainStyle}>
                    {this.renderItem()}
                </ScrollView>
            );
        },

        renderItem() {
            // 数组
            var itemAry = [];
            // 颜色数组
            var colorAry = ['gray', 'green', 'blue', 'yellow', 'black', 'orange'];
            // 遍历
            for (var i = 0; i<colorAry.length; i++) {
                itemAry.push(
                    <View key={i} style={[styles.itemStyle, {backgroundColor: colorAry[i]}]}></View>
                );
            }
            return itemAry;
        }
    });
    ```
    * 视图部分
    
    ```
    var styles = StyleSheet.create({
        scrollViewStyle: {
            // 背景色
            backgroundColor:'red'
        },

        itemStyle: {
            // 尺寸
            width:1000,
            height:200
        },
    });
    ```


##### 常用属性:
- contentContainerStyle：这些样式会引用到一个内层的内容容器上，所有的子视图都会包裹在内容容器内
 
- horizontal：当此属性为true的时候，所有的的子视图会在水平方向上排成一行，而不是默认的在垂直方向上排成一列。默认值为false
 
- keyboardDismissMode：用户拖拽滚动视图的时候，是否要隐藏软键盘。

    * none（默认值），拖拽时不隐藏软键盘
    * on-drag 当拖拽开始的时候隐藏软键盘
    * interactive 软键盘伴随拖拽操作同步地消失，并且如果往上滑动会恢复键盘。安卓设备上不支持这个选项，会表现的和none一样。
 
- keyboardShouldPersistTaps：当此属性为false的时候，在软键盘激活之后，点击焦点文本输入框以外的地方，键盘就会隐藏。如果为true，滚动视图不会响应点击操作，并且键盘不会自动消失。默认值为false
 
- refreshControl：指定RefreshControl组件，用于为ScrollView提供下拉刷新功能
 
- removeClippedSubviews：（实验特性）当此属性为true时，屏幕之外的子视图（子视图的overflow样式需要设为hidden）会被移除。这个可以提升大列表的滚动性能。默认值为true


- showsHorizontalScrollIndicator：当此属性为true的时候，显示一个水平方向的滚动条


- showsVerticalScrollIndicator：当此属性为true的时候，显示一个垂直方向的滚动条


- endFillColor：有时候滚动视图会占据比实际内容更多的空间。这种情况下可以使用此属性，指定以某种颜色来填充多余的空间，以避免设置背景和创建不必要的绘制开销。一般情况下并不需要这种高级优化技巧


- alwaysBounceHorizontal：当此属性为true时，水平方向即使内容比滚动视图本身还要小，也可以弹性地拉动一截。当horizontal={true}时(默认值为true)否则为false


- alwaysBounceVertical：当此属性为true时，垂直方向即使内容比滚动视图本身还要小，也可以弹性地拉动一截。当horizontal={true}时(默认值为false)，否则为true


- automaticallyAdjustContentInsets：如果滚动视图放在一个导航条或者工具条后面的时候，iOS系统是否要自动调整内容的范围。默认值为true。（译注：如果你的ScrollView或ListView的头部出现莫名其妙的空白，尝试将此属性置为false）


- bounces：当值为true时，如果内容范围比滚动视图本身大，在到达内容末尾的时候，可以弹性地拉动一截。如果为false，尾部的所有弹性都会被禁用，即使alwaysBounce*属性为true。默认值为true


- bouncesZoom：当值为true时，使用手势缩放内容可以超过min/max的限制，然后在手指抬起之后弹回min/max的缩放比例。否则的话，缩放不能超过限制

- canCancelContentTouches：当值为false时，一旦有子节点响应触摸操作，即使手指开始移动也不会拖动滚动视图。默认值为true（在以上情况下可以拖动滚动视图）


- centerContent：当值为true时，如果滚动视图的内容比视图本身小，则会自动把内容居中放置。当内容比滚动视图大的时候，此属性没有作用。默认值为false

- contentInset：{top: number, left: number, bottom: number, right: number}内容范围相对滚动视图边缘的坐标。默认为{0, 0, 0, 0}

- contentOffset：用来手动设置初始的滚动坐标。默认值为{x: 0, y: 0}


- onChangeText：当文本框内容变化时调用此回调函数。改变后的文字内容会作为参数传递

- decelerationRate：一个浮点数，用于决定当用户抬起手指之后，滚动视图减速停下的速度。常见的选项有：

    * Normal: 0.998 (默认值)
    * Fast: 0.9

    
- directionalLockEnabled：当值为真时，滚动视图在拖拽的时候会锁定只有垂直或水平方向可以滚动。默认值为false

- maximumZoomScale：允许的最大缩放比例。默认值为1.0

- minimumZoomScale：允许的最小缩放比例。默认值为1.0


- pagingEnabled：当值为true时，滚动条会停在滚动视图的尺寸的整数倍位置。这个可以用在水平分页上。默认值为false

- scrollEnabled：当值为false的时候，内容不能滚动，默认值为true

- scrollEventThrottle：这个属性控制在滚动过程中，scroll事件被调用的频率（单位是每秒事件数量）。更大的数值能够更及时的跟踪滚动位置，不过可能会带来性能问题，因为更多的信息会通过bridge传递。默认值为0，意味着每次视图被滚动，scroll事件只会被调用一次

- scrollIndicatorInsets：{top: number, left: number, bottom: number, right: number}决定滚动条距离视图边缘的坐标。这个值应该和contentInset一样。默认值为{0, 0, 0, 0}

- scrollsToTop：当此值为true时，点击状态栏的时候视图会滚动到顶部。默认值为true

- snapToAlignment：enum('start', "center", 'end')当设置了snapToInterval，snapToAlignment会定义停驻点与滚动视图之间的关系。

    * start (默认) 会将停驻点对齐在左侧（水平）或顶部（垂直）
    * center 会将停驻点对齐到中间
    * end 会将停驻点对齐到右侧（水平）或底部（垂直）
- snapToInterval：当设置了此属性时，会让滚动视图滚动停止后，停止在 snapToInterval 的倍数的位置。这可以在一些子视图比滚动视图本身小的时候用于实现分页显示 snapToAlignment 组合使用

- stickyHeaderIndices：一个子视图下标的数组，用于决定哪些成员会在滚动之后固定在屏幕顶端。举个例子，传递 stickyHeaderIndices={[0]} 会让第一个成员固定在滚动视图顶端。这个属性不能和 horizontal={true} 一起使用

- zoomScale：滚动视图内容初始的缩放比例。默认值为1.0

- onMomentumScrollEnd：当一帧滚动完毕的时候调用，通过 e.nativeEvent.contentOffset 获取偏移量

- onScrollBeginDrag：当开始手动拖拽的时候调用

- onScrollEndDrag：当结束手动拖拽的时候调用

- onScrollAnimationEnd：当滚动动画结束之后调用此回调

- onContentSizeChange：此函数会在ScrollView内部可滚动内容的视图发生变化时调用

    * 调用参数为内容视图的宽和高: (contentWidth, contentHeight)
    * 此方法是通过绑定在内容容器上的onLayout来实现的
- onScroll：在滚动的过程中，每帧最多调用一次此回调函数。调用的频率可以用scrollEventThrottle属性来控制(在Android不好使，而且影响性能

##### 常用方法:
- scrollTo：(y: number | { x?: number, y?: number, animated?: boolean }, x: number, animated: boolean)滚动到指定的x, y偏移处。第三个参数为是否启用平滑滚动动画

