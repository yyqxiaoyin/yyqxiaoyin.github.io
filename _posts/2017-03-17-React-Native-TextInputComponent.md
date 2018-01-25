---
title: React-Native学习记录（TextInput组件）
date: 2017-03-17 9:20:11
tags:
---
+ <!-- more -->

### TextInput组件介绍
- TextInput也是继承自 View,所以 View 的属性 TextInput 也能使用，一些样式类的属性可以参照 View 的相关属性

##### 属性方法:
- Value：文本输入的默认值（注：如果设置了此属性，会造成无法输入的尴尬，一般会搭配JS动态设置）
 
- keyboardType：设置键盘类型（决定使用哪种键盘）
 
- multiline：如果值为真，文本输入可以输入多行，默认值为假
 
- password：如果值为真，文本输入框就成为一个密码区域，默认值为假
 
- placeholder：在文本输入之前提示用户文本框功能，也就是占位文字
 
- placeholderTextColor：占位字符串的文本颜色
- autoCapitalize：控制TextInput是否要自动将特定字符切换为大写 none：不自动使用任何东西 sentences：每个句子的首字母（默认）words：每一个单词的首字母 characters：所有字符
- autoCorrect：如果为false，会关闭拼写自动修正。默认值是true。
- autoFocus：如果为true，在componentDidMount后会获得焦点。默认值为false。
- clearButtonMode：清除按钮出现的时机 never：不出现 while-editing：编辑的时候出现 unless-editing：没有编辑时出现 always：总是出现
- clearTextOnFocus：如果为true，每次开始输入的时候都会清除文本框的内容
- editable：如果值为假，文本是不可编辑，默认值为真
- enablesReturnKeyAutomatically：如果为true，键盘会在文本框内没有文字的时候禁用确认按钮。默认值为false。
- returnKeyType：决定返回键的样式

    * default
    * go
    * google
    * join
    * next
    * route
    * search
    * send
    * yahoo
    * done
    * emergency-call

- ecureTextEntry：如果值为真，文本输入框就会使输入的文本变模糊，以便于像密码这样敏感的文本保持安全，类似 password 属性，默认值为假
- onChange：当文本框内容变化时调用此回调函数

```
var textInputTest = React.createClass({
        render(){
            return(
                <View style={styles.container}>
                    {/* 文本输入框 */}
                    <TextInput
                        style={styles.textInputStyle}
                        onChange={() => {alert('文本框内容改变')}}
                    ></TextInput>
                </View>
            );
        }
    });
```
- onChangeText：当文本框内容变化时调用此回调函数。改变后的文字内容会作为参数传递

```
var textInputTest = React.createClass({
        render(){
            return(
                <View style={styles.container}>
                    {/* 文本输入框 */}
                    <TextInput
                        style={styles.textInputStyle}
                        onChangeText={(Text) => {alert('文字改变')}}
                    ></TextInput>
                </View>
            );
        }
    });
```
- onFocus：当文本框获得焦点的时候调用此回调函数

```
var textInputTest = React.createClass({
        render(){
            return(
                <View style={styles.container}>
                    {/* 文本输入框 */}
                    <TextInput
                        style={styles.textInputStyle}
                        onFocus={() => {alert('文本框获得焦点')}}
                    ></TextInput>
                </View>
            );
        }
    });
```

- onBlur：当文本框失去焦点的时候调用此回调函数

```
var textInputTest = React.createClass({
        render(){
            return(
                <View style={styles.container}>
                    {/* 文本输入框 */}
                    <TextInput
                        style={styles.textInputStyle}
                        onBlur={() => {alert('失去焦点')}}
                    ></TextInput>
                </View>
            );
        }
    });
```

- onEndEditing：结束编辑时，调用回调函数

```
var textInputTest = React.createClass({
        render(){
            return(
                <View style={styles.container}>
                    {/* 文本输入框 */}
                    <TextInput
                        style={styles.textInputStyle}
                        onEndEditing={() => {alert('结束文本编辑')}}
                    ></TextInput>
                </View>
            );
        }
    });
```

