---
name: FAQ
---

# FAQ

这里解答了一些经常被问到的问题。如果这些都没有解决您的问题，欢迎来到[Quaver官方Discord](https://discord.gg/pDbHYag)进行讨论解惑。

## 一般问题

### Quaver是什么？

Quaver是一个基于社区的开源竞技性音乐游戏，受到了各种经典的下落式音游的启发，并且计划在将来将其在实时竞技方面拓展。

### Quaver与其他游戏有什么不同？

Quaver是完全开源的，任何人都可以帮助改进这个游戏。我们希望能通过引入竞技这一概念（如竞技性比赛）提供一个全新的下落式音游体验。

### Quaver目前开发进度如何？

Quaver目前处于早期测试阶段（Early Access）。这意味着其核心功能已经完成了，所有人都可以自由地在线游玩。在这个阶段Quaver将接受频繁的更新，如bug修复与新特性增加。

### Quaver在哪些平台上发行？

Windows、Mac以及Linux。

## 游玩方式

### Quaver有哪些模式？

Quaver目前支持4键（4K）及7键（7K）模式。虽然支持7K+1（7键加一皿），但是在这个模式下得到的分数将一直为unranked状态。

### 谱面在哪里下载？

您可以用游戏内置下载器或在[Quaver网站](https://quavergame.com/maps)上下载。

### 我能导入其他游戏的谱面吗？

可以。Quaver目前支持.osz、.sm以及.mcz格式的谱面导入。将谱面文件拖入游戏窗口即可导入。

### 我在另一个音游有很多谱面，我能不能一次性将它们全部导入？

可以。在Quaver内找到Options > Miscellaneous，将“Load Songs From Other Installed Games”选项打开，然后点击 ”Detect Songs From Other Installed Games.“

### 我能导入别的游戏的皮肤吗？

这个游戏本身并不支持皮肤转换，但是您可以在[这里](https://rhythmgamers.net/QBC/)下载一个.osk皮肤转换器。这里是[使用教程](https://www.youtube.com/watch?v=pWeLbx48NVI)。

### 我找到了一个bug，我能在哪里汇报？

您应该在[GitHub issues](https://github.com/Quaver/Quaver/issues)上提交bug汇报。 您可以在上面自由发布任何您找的问题，但是请务必检查您汇报的问题是否已经有人汇报过了，以免造成重复汇报。

### 我有个新特性的想法，我能在哪里提供建议？

一样在[GitHub issues](https://github.com/Quaver/Quaver/issues)内即可。只需要在创建issue时选择“Feature Request”即可。

### 我能更改我的用户名吗？

更改用户名是捐助者特供的功能。如果你是捐助者，您可以每三十天更改一次用户名。

### 我如何在Linux下降低打击音效延迟？

一般情况下音频延迟应该不会出问题，但在一些不常见的情况下仍然可以进行微调。

如果您在游玩过程中感受到了音频延迟，打开`/etc/pulse/default.pa`，找到这样一行：

```
load-module module-udev-detect
```

将它改成：

```
load-module module-udev-detect fixed_latency_range=yes
```

然后重启系统。请注意这可能在一些特定应用有严重的音频卡顿现象（如在Firefox打开Discord，尽管其对应的组件以及有了一个修复）。

你还可以调整Quaver对系统要求的延迟。在`quaver.cfg`中找到这样一行：

```
DevicePeriod = 2
DeviceBufferLengthMultiplier = 4
```

以上为钟频率（系统对Quaver索取音频的频率，默认2毫秒）和缓冲长度（音频缓存大小，为钟频率的倍数，默认4）。将钟频率降低会减少音频延迟并增加CPU负担；减少缓冲长度可能会导致音频破裂等效果。将以上两项增加会增加音频延迟并减少CPU负担及音频卡顿的可能性。

### 我应该怎么用Wayland VSync？

首先需要一个带有Wayland Compositor的Linux系统，如较新的GNONE或KDE版本（请不要用Xorg模式），或用Western或Sway这类独立版本。

在Video/Linux下打开"Prefer Wayland"选项然后重启Quaver，然后将Wayland VSync打开。 您可以用FPS计数器确认它确实在运行。现在您的FPS应该等于您显示器的刷新频率，且UPS应该升高。

如果想要在Sway上调成最低延迟，在输出及Quaver窗口设置`max_render_time`。使用`man 5 sway`查看具体说明。

## 界面

### 怎么使用谱面筛选？

目前有以下这些谱面筛选参数：

| 筛选参数       | 短标签     | 长标签       | 参数                                                    |
| ------------ | ---------- | ----------- | ----------------------------------------------------------- |
| BPM          | b          | bpm         | 数字                                                      |
| 难度   | d          | difficulty  | 数字                                                     |
| 来源         | g          | game        | quaver/q, osu/o, stepmania/sm/s/etterna/e                   |
| 键数         | k          | keys        | 数字                                                      |
| 长度       | l          | length      | 秒数                                           |
| 长条（LN）数          | ln         | lns         | 数量(452)或占比(57%) |
| 键/秒       | n          | nps         | 数字                                                      |
| 状态       | s          | status      | ranked/r, notsubmitted/n, unranked/u, (dan/d)               |
| 游玩次数| t          | timesplayed | 数字                                                      |

所有筛选器可以使用`=` (等于)、`!=` (不等于)操作符， 对于以数字为参数的筛选器可以额外使用`>= > <= <`操作符。

筛选器输入方式为标签+操作符+参数，如`difficulty>30`。仅输入长标签开头一部分也可以接受，如`diff>30`。

如果只没有标签与操作符，仅提供参数，将筛选artist, title, mapper, tags栏内任意包含此参数的谱面。

只会返回符合全部筛选器要求的谱面(筛选器全与门)。目前没有对“或者”（筛选器或操作）的支持。

## 错误排查

### 无法打开游戏

Quaver依赖Steam运行，所以请确保Steam当前正在运行。

#### Linux、离线或本地构建

离线或发布的独立构建（如用`dotnet publish -c Release -r linux-x64`构建的版本）必须在Steam上才能运行。在Quaver仓库目录下运行以下命令：

```shell
~/.steam/bin/steam-runtime/run.sh Quaver/bin/Release/netcoreapp2.1/linux-x64/publish/Quaver
```

正常、非独立的构建（如用`dotnet build -p Quaver -c Debug`构建的版本）需要正确的库路径才能运行。这可以用Steam运行时启动脚本和Quaver自身的启动脚本完成：

```shell
~/.steam/bin/steam-runtime/run.sh Quaver/bin/Debug/netcoreapp2.1/quaver.sh
```

#### Windows 7

您需要一些额外的依赖库才能在Windows 7上运行.NET Core。

在[这个](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31&pivots=os-windows#additional-deps)站点下按照“Install the following”下的步骤操作即可。

### 在尝试下载Quaver时提示“内容文件锁定”

这可能是与Steam有关的问题。

一些可能能修复此问题的方案是：以管理员身份运行Steam；重启电脑；验证Quaver文件完整性。

如果以上方案都没有解决问题，那么在以下几个帖子里可能会有答案：

- [帖子1（Steam社区）](https://steamcommunity.com/app/346110/discussions/0/333656722964822410/)
- [帖子2（Reddit）](https://www.reddit.com/r/Steam/comments/5cnjzf/content_file_locked/)

### Quaver启动时分辨率大于我显示器的分辨率导致玩不了

如果您的游戏出现了这个问题，请先关闭Quaver，然后找到Quaver的Steam本地文件路径。

打开`quaver.cfg`然后找到`WindowHeight`（窗口高度）、`WindowWidth`（窗口宽度）及`WindowFullScreen`（全屏）配置选项，然后设置成你希望的分辨率。为了避免额外的问题，请在Quaver再次启动之前请先将`WindowFullScreen` 设置成False。

### 我的杀毒软件把Quaver当成恶意的

这是电子证书需要购买以及维护成本，游戏文件没有电子签名导致的。

为避免Quaver被误认，请将`Quaver.exe`或其所在的文件夹加入您的杀毒软件的白名单。
