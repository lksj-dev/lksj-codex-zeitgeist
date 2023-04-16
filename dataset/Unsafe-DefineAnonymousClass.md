

## 症状

安装 Forge 后游戏无法启动，日志中有如下字样：

```
java.lang.NoSuchMethodException: no such method: sun.misc.Unsafe.defineAnonymousClass(Class,byte[],Object[])Class/invokeVirtual
```

## 成因

适用于 1.16 的 Forge 不支持使用 Java 17 及以上版本。

## 技术分析 

*TODO: Need a better explanation for this.*

Java 15 起开始弃用 `sun.misc.Unsafe#defineAnonymousClass`，并于 Java 17 完成移除。

## 解决方案

对于 1.17（更准确地说，21w19a）以下的版本，应使用 Java 8 启动游戏。