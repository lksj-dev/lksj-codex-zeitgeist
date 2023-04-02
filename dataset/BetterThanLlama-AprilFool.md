
## 症状

游戏崩溃，系统时间是 4 月 1 日附近，栈帧形如：

```
java.lang.NullPointerException: Cannot invoke "net.minecraft.world.level.Level.m_46658_()" because "p_21369_" is null
	at TRANSFORMER/minecraft@1.18.2/net.minecraft.world.entity.Mob.<init>(Mob.java:117)
	at TRANSFORMER/minecraft@1.18.2/net.minecraft.world.entity.PathfinderMob.<init>(PathfinderMob.java:14)
	at TRANSFORMER/minecraft@1.18.2/net.minecraft.world.entity.AgeableMob.<init>(AgeableMob.java:28)
	at TRANSFORMER/minecraft@1.18.2/net.minecraft.world.entity.animal.Animal.<init>(Animal.java:40)
	at TRANSFORMER/minecraft@1.18.2/net.minecraft.world.entity.animal.Rabbit.<init>(Rabbit.java:88)
	at TRANSFORMER/betterthanllamas@1.1.1/me.ichun.mods.betterthanllamas.client.render.LlamaFancyLayer.<init>(LlamaFancyLayer.java:69)
	at TRANSFORMER/betterthanllamas@1.1.1/me.ichun.mods.betterthanllamas.common.BetterThanLlamas.onAddLayers(BetterThanLlamas.java:94)
	at MC-BOOTSTRAP/eventbus@5.0.3/net.minecraftforge.eventbus.EventBus.doCastFilter(EventBus.java:247)
	at MC-BOOTSTRAP/eventbus@5.0.3/net.minecraftforge.eventbus.EventBus.lambda$addListener$11(EventBus.java:239)
	at MC-BOOTSTRAP/eventbus@5.0.3/net.minecraftforge.eventbus.EventBus.post(EventBus.java:302)
	at MC-BOOTSTRAP/eventbus@5.0.3/net.minecraftforge.eventbus.EventBus.post(EventBus.java:283)
	at LAYER PLUGIN/javafmllanguage@1.18.2-40.1.84/net.minecraftforge.fml.javafmlmod.FMLModContainer.acceptEvent(FMLModContainer.java:106)
```

## 成因

iChun 的 Better Than Llamas 模组存在 Bug，会导致其本应于公历 4 月 1 日启用的愚人节彩蛋引发游戏崩溃。

## 技术分析 

参考该 Pull Request：https://github.com/iChun/BetterThanLlamas/pull/4

## 解决方案

更新 Better Than Llamas 模组到至少 1.2.0 版。

若无法更新模组，等待愚人节过去即可。亦可直接禁用该彩蛋以避免问题（待查：是否支持禁用？）。

## 备注

该问题在其 Issue tracker 中有明确记录：https://github.com/iChun/BetterThanLlamas/issues/3