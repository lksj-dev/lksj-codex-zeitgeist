

## 症状

游戏崩溃，日志中有如下字样：

```
java.lang.NullPointerException: Ticking entity
	at java.base/java.util.Objects.requireNonNull(Objects.java:208)
	at nova.committee.enhancedarmaments.init.handler.LivingHurtEventHandler.lambda$onArrowHit$0(LivingHurtEventHandler.java:41)
	at nova.committee.enhancedarmaments.init.callback.ProjectileImpactCallback.lambda$static$0(ProjectileImpactCallback.java:17)
	at net.minecraft.class_1676.handler$bfl000$enhancedarmaments$port_lib$onProjectileHit(class_1676.java:523)
```

## 成因

Enchanted Armaments Reloaded 版本过低。

## 技术分析 

https://github.com/Nova-Committee/Enhanced-Armaments-Reload/commit/6275d2e124a122964583b493241dce2724fbf997

## 解决方案

更新 Enhanced Armaments Reloaded 到 1.19-1.1.3 或更高版本。