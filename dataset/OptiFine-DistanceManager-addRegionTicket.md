
## 症状

游戏崩溃，崩溃报告给出的栈帧形如：

```
java.lang.NoSuchMethodError: 'void net.minecraft.server.level.DistanceManager.addRegionTicket(net.minecraft.server.level.TicketType, net.minecraft.world.level.ChunkPos, int, java.lang.Object, boolean)'
	at net.minecraft.server.level.ServerChunkCache.addRegionTicket(ServerChunkCache.java:429) ~[client-1.18.2-20220404.173914-srg.jar%2355!/:?] {re:classloading,pl:accesstransformer:B}
	at net.minecraft.server.level.ServerChunkCache.m_8387_(ServerChunkCache.java:425) ~[client-1.18.2-20220404.173914-srg.jar%2355!/:?] {re:classloading,pl:accesstransformer:B}
	at net.minecraft.server.MinecraftServer.m_129940_(MinecraftServer.java:471) ~[client-1.18.2-20220404.173914-srg.jar%2355!/:?] {re:classloading,pl:accesstransformer:B}
	at net.minecraft.server.MinecraftServer.m_130006_(MinecraftServer.java:318) ~[client-1.18.2-20220404.173914-srg.jar%2355!/:?] {re:classloading,pl:accesstransformer:B}
	at net.minecraft.client.server.IntegratedServer.m_7038_(IntegratedServer.java:84) ~[client-1.18.2-20220404.173914-srg.jar%2355!/:?] {re:classloading,xf:OptiFine:default}
	at net.minecraft.server.MinecraftServer.m_130011_(MinecraftServer.java:661) ~[client-1.18.2-20220404.173914-srg.jar%2355!/:?] {re:classloading,pl:accesstransformer:B}
	at net.minecraft.server.MinecraftServer.m_177918_(MinecraftServer.java:261) ~[client-1.18.2-20220404.173914-srg.jar%2355!/:?] {re:classloading,pl:accesstransformer:B}
	at java.lang.Thread.run(Thread.java:833) ~[?:?] {}
```

## 成因

适用于 1.18.2 的 OptiFine 与 Forge 的某些版本不兼容。

## 技术分析

无

## 解决方案

升级 OptiFine 到 1.18.2 H9 pre2 版本。
