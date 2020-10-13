## 如何进行WebView的性能优化
Android端：

1. **为WebView单开一个进程**，通过AIDL与应用的主进程进行通讯

2. **将js本地化打包进apk中**，通过shouildInterceptRequest拦截加载，前端也配合用懒加载js脚本；

3. 采用**X5WebView**内核，增加版本兼容性的错误，提升速度；

4. 不在xml中创建WebView，而是**动态地创建**，引用applicationContext，再加入到布局；这个问题是，onJsAlert会失败

5. 因为WebView首次加载特别慢，**在空闲的时候创建一次WebView再销毁**，来加快WebView加载的速度

6. WebSettings的setCacheMode()缓存模式，**在无网络的时候设置为LOAD_CACHE_ONLY，有网络时设置为LOAD_DEFAULT**，达到离线加载的结果

7. 在WebSettings几个重要的**缓存**功能都打开

其他端：

1. 让前端，使用懒加载js脚本

2. 使用CDN服务

3. 前端图片采用webp

## WebView的原理是什么？（Java如何实现和Js通讯的？）


待完成...


## 如何解决WebView内存泄漏的问题？

1. 为WebView单独开一个进程

2. 不在XML中定义WebView，每次使用前new出来，传入applicationContext


## 使用WebView的过程中遇到哪些难点？

1. 需要处理登录状态同步的问题，用户在客户端登录，需要把登录状态同步到WebView，避免二次登录；通过OKHttp的CookieJar获取到Cookie，保存到SharedPreferences，然后通过CookieSyncManager同步到WebView

2. 对于WebView内存泄露的问题，采用了两个措施，↑↑↑

3. 关于提高WebView的首屏加载速度，采用了js本地化的方案


## 链接
[QQ：70%以上业务由H5开发，手机QQ Hybrid 的架构如何优化演进？（深入）](https://mp.weixin.qq.com/s/evzDnTsHrAr2b9jcevwBzA?)


[美团：WebView性能、体验分析与优化（深入）](https://tech.meituan.com/2017/06/09/webviewperf.html)


[CSDN：腾讯祭出大招VasSonic，让你的H5页面首屏秒开（不错）](https://blog.csdn.net/tencent__open/article/details/77324952)


[CSDN：VasSonic简单介绍](https://blog.csdn.net/oqzuser1587576/article/details/87975943)


[掘金：Android WebView：性能优化不得不说的事](https://juejin.im/entry/57d6434067f3560057e50b20)

[简书：WebView加载速度优化](https://www.jianshu.com/p/427600ca2107)


[简书：Android WebView独立进程解决方案](https://www.jianshu.com/p/b66c225c19e2)


[CSDN：优化Webview加载速度 TBS\(腾讯浏览服务X5内核\) | VasSonic\(提升H5首屏加载速度\)](https://blog.csdn.net/u012982629/article/details/81357154)


[CSDN：实战 | 封装解决WebView的那些坑](https://blog.csdn.net/developandroid/article/details/73280151)


[简书：Android-X5WebView封装（Cookie管理、进度监听、适配8.1系统等策略）（踩坑系列）](https://www.jianshu.com/p/88084a66c256)