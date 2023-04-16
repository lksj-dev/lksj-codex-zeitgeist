
## 症状

安装 Forge 和其他模组后的游戏无法启动，崩溃报告中有如下字样：

```
java.lang.IllegalArgumentException: No model for layer pyrotastic:firework_rocket#base
```

## 成因

有其他错误导致游戏无法正常加载，但在 Forge 成功显示「游戏加载出错」界面之前，Pyrotastic 出现了另一个错误导致原错误被掩盖。

## 技术分析 

暂缺

## 解决方案

无，因为 Pyrotastic 并非导致此问题的 Mod。请往上翻阅日志以寻找真正的原因。

通常，出现此崩溃的原因是因为缺失前置，这一点可通过日志中的 `Error during pre-loading phase` 以及 `net.minecraftforge.fml.ModLoadingException` 字样加以证实。
但从理论上来说，任何能导致 FML 抛出 `net.minecraftforge.fml.ModLoadingException` 的错误均可触发 Pyrotastic 的这个问题，所以遇到此问题时，必须根据实际情况分析。

