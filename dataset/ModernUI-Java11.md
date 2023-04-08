
## 症状

游戏无法启动，日志中有如下字样

```
java.lang.UnsupportedClassVersionError: icyllis/modernui/forge/MixinConnector has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0
```

## 成因

[ModernUI](https://github.com/BloCamLimb/ModernUI) 需要 Java 11 或以上版本。

## 技术分析 

适用于 1.16.5 的 ModernUI 编译时使用的 target compatiblity 为 Java 11，因此编译出来的 class 文件中的 major.minor 版本号为 `55.0`。

相应的，Java 8 对应的 class 文件 major.minor 版本号为 `52.0`，最高也只能兼容到此版本。出现 `this version of the Java Runtime only recognizes class file versions up to 52.0` 字样即说明当事人使用了 Java 8。

更多信息可参考：https://stackoverflow.com/questions/9170832/list-of-java-class-file-format-major-version-numbers

## 解决方案

使用 Java 11 或以上版本启动游戏，或直接删除 ModernUI 及所有硬依赖 ModernUI 的 Mod。