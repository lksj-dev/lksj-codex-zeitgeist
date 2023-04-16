
## 症状

游戏版本 1.16.5，安装 Timeless and Classics 和 Valkyrien Skies 后，在进入世界时崩溃，日志中有如下字样

```
java.lang.NoSuchFieldError: EXACT_FLOATS
	at com.fasterxml.jackson.dataformat.cbor.CBORParser.<clinit>(CBORParser.java:73) ~[valkyrienskies:?]
	at com.fasterxml.jackson.dataformat.cbor.CBORParserBootstrapper.constructParser(CBORParserBootstrapper.java:93) ~[valkyrienskies:?]
	at com.fasterxml.jackson.dataformat.cbor.CBORFactory._createParser(CBORFactory.java:400) ~[valkyrienskies:?]
	at com.fasterxml.jackson.dataformat.cbor.CBORFactory.createParser(CBORFactory.java:325) ~[valkyrienskies:?]
	at com.fasterxml.jackson.dataformat.cbor.CBORFactory.createParser(CBORFactory.java:27) ~[valkyrienskies:?]
	at com.fasterxml.jackson.databind.ObjectMapper.readValue(ObjectMapper.java:3667) ~[tac:**.**.**.**-1.16.5]
	at org.valkyrienskies.core.util.serialization.VSJacksonUtilKt.readValue(VSJacksonUtil.kt:113) ~[valkyrienskies:?]
```

## 成因

适用于 Minecraft 1.16.5 的 Timeless and Classics 和 Valkyrien Skies 互相冲突。

## 技术分析

Timeless and Classics 和 Valkyrien Skies 均打包了 `jackson-core`，而 `jackson-core` 在 2.14 版本引入了一个新的枚举字段：`StreamReadCapability.EXACT_FLOAT`：

https://github.com/FasterXML/jackson-core/commit/e655e46e61d20340924128b2bcdf9466600d1aea

虽然 Valkyrien Skies 声明的 `jackson-databind` 版本是 2.13.3，但根据拆包结果来看，其作为 transitive dependency 打包的 `jackson-core` 的版本是 2.14.0。
与此同时，Timeless and Classics 打包入的 `jackson-core` 版本未知，但肯定小于 2.14.0，因为从其中提取的 `StreamReadCapability` 中没有 `EXCAT_FLOATS` 字段。

Timeless and Classics 和 Valkyrien Skies 都没有对其打包结果进行 Relocation，意味着当玩家同时安装这两个 Mod 时，如果加载到了 Timeless and Classics 打包的旧版 `StreamReadCapability.class`，但 `CBORParser` 等类却是来自 Valkyrien Skies 打包的新版，那么就会出现版本不一致的问题，导致「本应存在的字段实际上根本不存在」，进而导致崩溃。

## 解决方案

无有效解决方案。最有效的解决方案是写一个空 Mod，通过显式声明加载顺序，强制让 Valkyrien Skies 在 Timeless and Classics 之前加载，然而出现此问题的 Minecraft 1.16.5 上并没有预装有 `lowcode` Language Adapter 的 Forge/FML，所以必须有一个空的带 `@Mod` 注解的类。

## 备注

已反馈回上游：

https://github.com/ClumsyAlien/TimelessandClassics_Reforged/issues/81
https://github.com/ValkyrienSkies/Valkyrien-Skies-2/issues/448