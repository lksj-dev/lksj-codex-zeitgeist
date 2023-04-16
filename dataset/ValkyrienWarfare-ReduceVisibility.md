
## 症状

```
org.spongepowered.asm.mixin.transformer.throwables.InvalidMixinException: PROTECTED @Overwrite method func_174806_f in mixins.valkyrienwarfare.json:entity.MixinEntity cannot reduce visibiliy of PUBLIC target method
```

## 成因

Valkyrien Warfare 和 Tinkers Evolution 不兼容

## 技术分析

Tinker's Evolution 通过 AT 提升了 `Entity.getVectorForRotation`（SRG `func_174806_f`）的访问级：

https://github.com/phantamanta44/tinkers-evolution/blob/1.12.2/src/main/resources/META-INF/tconevo_at.cfg

然而 Valkyrien Warfare 使用 Mixin 完全重写（即 `@Overwrite`）`func_174806_f` 时仍保留了其原本的 `protected` 访问级，进而产生冲突。

https://github.com/ValkyrienSkies/Valkyrien-Skies/commit/f1ef708e8e9e8a425949558a12757afa6e46a7fb

## 解决方案

更新 Valkyrien Warfare。

## 备注

Valkyrien Warfare 现已改名为 Valkyrien Skies。

Valkyrien Warfare 和 Tinker's Evolution 不兼容的问题有明确记录：

https://github.com/ValkyrienSkies/Valkyrien-Skies/issues/437