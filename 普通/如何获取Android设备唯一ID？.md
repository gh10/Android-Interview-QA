## 类型

#### 1. IMEI
权限(读手机权限)
可以手动更改(模拟器上) /关闭权限报错

#### 2. Mac 地址
访问 WIFI 权限
有些设备没有 wifi(没有上网功能)/6.0以上版本返回的都是固定的 02:00:00 之类地址

#### 3. ANDROID_ID
设备首次运行，系统会随机生成一个 64 位的数字，转换成 16 进制保存
手机恢复出厂设置后值有变化/有些国产设备不会返回值

#### 4. Serial Number/SN 号 (设备序列号)
有些国产手机(红米)会出现垃圾数据


## 实现思路

1. 获取设备的 IMEI -> 设备的 Mac 地址->随机生成的 UUID,

2. 拼接在一起，然后用 MD5 加密

3. 存储到本地的文件中，隐藏。并且存储在 App 中的 sp 中

4. 使用的时候先从 sp 中读取, 没有的再生成,然后把生成的唯一 id 保存到 sp 中


## 链接
[GitHub：每日一题](https://github.com/Moosphan/Android-Daily-Interview/issues/159)