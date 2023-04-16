

## 症状

游戏无法启动，日志中有如下字样：

```
java.lang.IllegalArgumentException: Unsupported class file major version 64
	at org.objectweb.asm@9.3.0/org.objectweb.asm.ClassReader.<init>(ClassReader.java:199)
```

## 成因

用户使用 Java 20 启动游戏。

## 技术分析

Forge 1.19.4 使用的 ASM 9.3.0 仍不支持 major version 为 64 的 class 文件，而 major version 64 对应的 Java 大版本号是 20。

## 解决方案

1.18 及更高版本的 Minecraft 应使用 Java 17 启动。

<!-- TODO 未来若 Minecraft 继续提高 Java 版本要求，这里的说明也应该随之更新。 -->