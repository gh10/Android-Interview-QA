## 原因
#### 1. 字符串常量池的需要
当创建一个 String 对象时，如果此字符串已经存在于常量池中，则不会创建一个新的对象，而是引用已经存在的对象。如果允许改变，那么将导致各种逻辑错误，比如改变一个对象将会影响另一个独立对象，严格来说，这种常量池的思想是一种优化手段

#### 2. 允许 String 对象缓存 HashCode
Java 中 String 对象的哈希码会被频繁的使用，比如在 HashMap 中。字符串的不变形保证了 hash 码的唯一性，因此可以放放心的进行缓存。这也是一种优化手段，意味着不必没说都计算新的哈希码，在 String 类中有 private int hash 来缓存 hashcode

#### 3. 安全性
String 被许多的类来当做参数，如网络 url，文件路径 path 等等，如果 String 不是固定的，将会引起各种安全隐患

#### 4. 线程安全
String 不可变性天生具备线程安全，可以在多个线程中安全地使用。

## 目的

* 性能优化（常量池存储，字符串不变保证了 Hashcode 唯一性）
* 安全性（考虑类加载的关系，多线程使用时，网络请求时 url 地址）

## 链接

[Github：String为什么要设计成不可变的？](https://github.com/Moosphan/Android-Daily-Interview/issues/153)