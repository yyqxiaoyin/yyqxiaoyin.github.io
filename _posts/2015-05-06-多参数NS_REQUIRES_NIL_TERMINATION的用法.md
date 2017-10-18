---
title: 多参数NS_REQUIRES_NIL_TERMINATION的用法

date: 2015-05-06 14:29:06
tags:
---
+ <!-- more -->


<pre>
#if !defined(NS_REQUIRES_NIL_TERMINATION)
    #if TARGET_OS_WIN32
        #define NS_REQUIRES_NIL_TERMINATION
    #else
        #if defined(__APPLE_CC__) && (__APPLE_CC__ >= 5549)
            #define NS_REQUIRES_NIL_TERMINATION __attribute__((sentinel(0,1)))
        #else
            #define NS_REQUIRES_NIL_TERMINATION __attribute__((sentinel))
        #endif
    #endif
#endif
</pre>

NS_REQUIRES_NIL_TERMINATTION 是系统中多参数传值的一个宏，用于编译时非nil结尾的检查

使用示例：

<pre>-(void)arrayWithObjects:(id)firstObj, ... NS_REQUIRES_NIL_TERMINATION;</pre>

实现原理

<pre>
-(void)arrayWithObjects:(id)firstObj, ...{
    
    NSMutableArray* arrays = [NSMutableArray array];
    //VA_LIST 是在C语言中解决变参问题的一组宏
    va_list argList;
    
    if (firstObj) {
        [arrays addObject:firstObj];
        // VA_START宏，获取可变参数列表的第一个参数的地址,在这里是获取firstObj的内存地址,这时argList的指针 指向firstObj
        va_start(argList, firstObj);
        // 临时指针变量
        id temp;
        // VA_ARG宏，获取可变参数的当前参数，返回指定类型并将指针指向下一参数
        // 首先 argList的内存地址指向的fristObj将对应储存的值取出,如果不为nil则判断为真,将取出的值房在数组中,
//        并且将指针指向下一个参数,这样每次循环argList所代表的指针偏移量就不断下移直到取出nil
        while ((temp = va_arg(argList, id))) {
            [arrays addObject:temp];
            
        }
        
    }
    // 清空列表
    va_end(argList);
}
</pre>