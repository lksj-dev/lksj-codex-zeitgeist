
## 症状

安装 Forge 后游戏无法启动，日志中有如下字样：

```
java.lang.IllegalAccessError: class cpw.mods.modlauncher.SecureJarHandler (in unnamed module @0x343570b7) cannot access class sun.security.util.ManifestEntryVerifier (in module java.base) because module java.base does not export sun.security.util to unnamed module @0x343570b7
```

## 成因

适用于 1.16 的 Forge 不支持使用 Java 17 及以上版本。

## 技术分析 

*TODO: Need a better explanation for this.*

在 Java 9 引入 Java Platform Module System 后，对于 `sun.*` 等 JDK 内部实现的访问控制日渐收紧（表现为 `java.base` 模块默认不开放内部实现给外界），而 Forge 的某些功能（尤其是实现基于 NIO 的签名验证）不得不需要引用 `sun.*` 等实现细节。

## 解决方案

对于 1.17（更准确地说，21w19a）以下的版本，应使用 Java 8 启动游戏。