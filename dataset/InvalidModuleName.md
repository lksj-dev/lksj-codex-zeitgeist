
## 症状

游戏无法启动，日志中有如下字样：

```
java.lang.IllegalArgumentException: : Invalid module name: '' is not a Java identifier
```

## 成因

当事人改动了 Mod 文件的文件名。

## 技术分析 

*TODO: Check since when Forge adopts SecureJarHandler.*

Forge 默认会通过 [SecureJarHandler][ref-1] 把每一个 Jar 都当做一个 [JPMS][ref-2] 的模块（Module）加载。和 [Java SE 所描述的过程一样][ref-2]，SecureJarHandler 首先会查找 `module-info` 并使用其中给出的信息决定模块名，并在找不到 `module-info` 的情况下，使用如下顺序决定模块名：

  1. 读取 `META-INF/MANIFEST.MF` 里的 `Automatic-Module-Name` 属性（Attribute），若存在则使用该属性的值作为模块名；
  2. 根据文件名生成，过程如下：
    1. 先去掉文件名里的 `.jar` 后缀名；
    2. 检查是否有 -(\\d+(\\.|$)) 的部分，有的话只取 - 前面的部分，- 后面的部分成为该模块的版本号
    3. 把不是拉丁字母和数字的字符（正则表达式 `[^A-Za-z0-9]`）都换成点；
    4. 把连续的多个点换成一个点；
    5. 最后去掉开头和结尾的点。

按照 2.，如果你的文件名是 `暮色森林.jar`，那么这么一通流程下来，你得到的模块名会是空字符串，而根据 [JLS 9 中对模块声明的要求][ref-3]，空字符串不可用作 [Identifier][ref-4]。

[ref-1]: https://github.com/McModLauncher/securejarhandler
[ref-2]: https://openjdk.org/projects/jigsaw/spec/
[ref-3]: https://docs.oracle.com/javase/9/docs/api/java/lang/module/ModuleFinder.html#of-java.nio.file.Path...-
[ref-4]: https://docs.oracle.com/javase/specs/jls/se9/html/jls-7.html#jls-7.7
[ref-5]: https://docs.oracle.com/javase/specs/jls/se9/html/jls-3.html#jls-Identifier

## 解决方案

不要重命名任何你下载回来的 Mod。