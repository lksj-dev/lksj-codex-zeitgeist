
## 症状

游戏无法启动，日志中有如下字样

```
[03:51:49] [main/WARN]: @Redirect conflict. Skipping dungeons_gear.mixins.json:GameRendererMixin->@Redirect::getModifiedDistance1(Lnet/minecraft/util/math/vector/Vector3d;Lnet/minecraft/util/math/vector/Vector3d;)D with priority 1000, already redirected by valkyrienskies-common.mixins.json:client.renderer.MixinGameRenderer->@Redirect::correctDistanceChecks(Lnet/minecraft/util/math/vector/Vector3d;Lnet/minecraft/util/math/vector/Vector3d;)D with priority 1000
[03:51:49] [main/WARN]: @Redirect conflict. Skipping dungeons_gear.mixins.json:GameRendererMixin->@Redirect::getModifiedDistance2(Lnet/minecraft/util/math/vector/Vector3d;Lnet/minecraft/util/math/vector/Vector3d;)D with priority 1000, already redirected by valkyrienskies-common.mixins.json:client.renderer.MixinGameRenderer->@Redirect::correctDistanceChecks(Lnet/minecraft/util/math/vector/Vector3d;Lnet/minecraft/util/math/vector/Vector3d;)D with priority 1000
```

```
org.spongepowered.asm.mixin.injection.throwables.InjectionError: Critical injection failure: Redirector getModifiedDistance1(Lnet/minecraft/util/math/vector/Vector3d;Lnet/minecraft/util/math/vector/Vector3d;)D in dungeons_gear.mixins.json:GameRendererMixin failed injection check, (0/1) succeeded. Scanned 1 target(s). Using refmap dungeons_gear.refmap.json
```

## 成因

Dungeon Gears 和 Valkyrien Skies 2 不兼容。

## 技术分析

暂缺（和 `@Redirect` 不支持嵌套有关）

## 解决方案

暂无，截至目前只能二选一。

## 备注

该问题在 Dungeon Gears 和 Valkyrien Skies 的 Issue tracker 中皆有明确记录：

https://github.com/Infamous-Misadventures/Dungeons-Gear/issues/173

https://github.com/ValkyrienSkies/Valkyrien-Skies-2/issues/232