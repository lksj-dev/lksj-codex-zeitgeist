
## 症状

游戏无法启动，日志中有如下字样

```
org.spongepowered.asm.mixin.injection.throwables.InjectionError: Critical injection failure: Redirector flytre_lib$auth_me(Ljava/lang/String;Ljava/lang/String;Ljava/lang/String;Ljava/util/Optional;Ljava/util/Optional;Lnet/minecraft/class_320$class_321;)Lnet/minecraft/class_320; in flytre_lib.mixins.json:config.MainMixin from mod flytre_lib failed injection check, (0/1) succeeded. Scanned 1 target(s). Using refmap flytre_lib-1.19-1.8.6-fabric-refmap.json
```

## 成因

FlytreLib 1.19-1.8.6、1.19-1.8.7、1.19-1.8.8 不兼容 1.19.2。

## 技术分析

暂缺

## 解决方案

无，因为 FlytreLib 截至目前（2023 年 4 月 14 日）还没有发布适用于 Minecraft 1.19.2 的版本。

请卸载 FlytreLib 以及所有要求 FlytreLib 的模组，或降级 Minecraft 到 1.19.1。