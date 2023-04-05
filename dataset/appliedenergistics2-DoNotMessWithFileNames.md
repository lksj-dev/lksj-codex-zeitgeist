
## 症状

游戏崩溃，系统时间是 9 月 25 日附近，栈帧形如：

```
Description: There was a severe problem during mod loading that has caused the game to fail

net.minecraftforge.fml.common.LoaderException: enderioconduitsappliedenergistics Failed to load new mod instance.
```
……

```
       | LE    | enderioconduitsappliedenergistics | 5.2.60             | EnderIO-1.12.2-5.2.60.jar                              | None                     
```

```
        | L     | appliedenergistics2               | rv6-stable-7       | 【应用能源1.12】appliedenergistics2-rv6-stable-7.jar         | None                                     |
```

## 成因

某些启动器和用户乱改mod的文件名，导致加载顺序错乱而崩溃。

## 技术分析 

我经常给人看这篇问答帖，常看常新。https://bbs.mcmod.cn/thread-4159-1-1.html

## 解决方案

恢复各模组原本的文件名，尤其是确保模组和前置之间的先后关系。

## 备注

我印象里原本这里说的比现在的版本还要生动夸张，这个帖子的答案可能被编辑过。