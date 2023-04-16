
## 症状

游戏崩溃退出，崩溃日志中有如下字样

```
java.lang.NoSuchMethodError: net.minecraft.entity.Entity.getDimensionsForge(Lnet/minecraft/entity/Pose;)Lnet/minecraft/entity/EntitySize;
```

## 成因

Forge 版本过低。

## 技术分析 

当事人使用的 Mod 中，有至少一个 Mod 使用了 [Forge 36.2.39（适用于 Minecraft 1.16.5）新引入的方法][ref-1]但没有声明版本要求，而当事人的 Forge 不是 36.2.39 或更高版本。

[ref-1]: https://github.com/MinecraftForge/MinecraftForge/pull/8668

## 解决方案

更新 Forge 到 36.2.39 或更高版本。