## 症状

安装 Forge 后游戏无法启动，日志中可找到如下字样（可全字匹配）：

```
java.lang.NoSuchMethodError: sun.security.util.ManifestEntryVerifier.<init>(Ljava/util/jar/Manifest;)V
```

## 成因

旧版 Forge 所使用的 Modlauncher（8.1.3 及更古早版本）与 JDK 8u321 或更新版本的 JDK 8 不兼容。

## 技术分析 

https://github.com/McModLauncher/modlauncher/issues/91

## 解决方案

更新 Forge 到 36.2.26 或以上版本。