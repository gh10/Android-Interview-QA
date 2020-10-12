### 原理

热修复分为三个部分，分别是Java代码部分热修复，Native代码部分热修复，还有资源热修复。

##### 1. 资源热修复

资源部分热更新直接反射更改所有保存的AssetManager和Resources对象就行（可能需要重启应用）

##### 2. Native热修复

Native代码部分也很简单，系统找到一个so文件的路径是根据ClassLoader找的，修改ClassLoader里保存的路径就行（可能需要重启应用）

##### 3. Java热修复

Java部分的话目前主流有两种方式，一种是Java派，一种是Native派。

1. Java派：通过修改ClassLoader来让系统优先加载补丁包里的类
代表作有腾讯的tinker，谷歌官方的Instant Run，包括multidex也是采用的这种方案
优点是稳定性较好，缺点是可能需要重启应用

2. Native派：通过内存操作实现，比如方法替换等
代表作是阿里的SopHix，如果算上hook框架的话，还有dexposed，epic等等
优点是即时生效无需重启，缺点是稳定性不好：
如果采用方法替换方式实现，假如这个方法被内联/Sharpening优化了，那么就失效了；inline hook则无法修改超短方法。
热修复后使用反射调用对应方法时可能发生IllegalArgumentException。

### 链接

[Github每日一题：](https://github.com/Moosphan/Android-Daily-Interview/issues/73)



[刘望舒：Android解析ClassLoader（二）Android中的ClassLoader](http://liuwangshu.cn/application/classloader/2-android-classloader.html)


[掘金：热修复——深入浅出原理与实现（Good）](https://juejin.im/post/5a0ad2b551882531sba1077a2#heading-4)


[我为Dexposed续一秒——论ART上运行时 Method AOP实现（epic详细讲解，非常深入，值得研究）](http://weishu.me/2017/11/23/dexposed-on-art/)


[Github：epic](https://github.com/tiann/epic)


[CSDN：Android 热补丁技术——资源的热修复（Good）](https://blog.csdn.net/sbsujjbcy/article/details/52541803)


[简书：Android 插件化和热修复知识梳理](https://www.jianshu.com/p/704cac3eb13d)


[掘金：我的Android重构之旅：插件化篇](https://juejin.im/post/5b42b89ae51d451906123b44#comment)


[Github：VirtualAPK](https://github.com/didi/VirtualAPK)


[简书：理解 Android Hook 技术以及简单实战](https://www.jianshu.com/p/4f6d20076)