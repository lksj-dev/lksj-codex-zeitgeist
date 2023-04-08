
## 症状

游戏崩溃，栈帧形如：

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

某些启动器和用户乱改mod的文件名，导致加载顺序错乱而崩溃。因为coremod的加载是按照文件名顺序来的，所以如果修改了文件名，可能会导致前置模组没能及时加载，就加载了依赖他们的模组而ClassNotFound之类的。

## 技术分析 

我经常给人看这篇问答帖，常看常新。

## 解决方案

恢复各模组原本的文件名，尤其是确保模组和前置之间的先后关系。

## 备注

出自https://bbs.mcmod.cn/thread-4159-1-1.html。
我印象里原本这里说的话比现在的版本还要生动夸张（“偏偏某些地方下载的整合包就是喜欢加这样的前缀”），这个帖子的答案可能被编辑过。