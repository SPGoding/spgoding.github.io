---
layout: post
title: Minecraft：Java 版命令返回值列表
date: 2021-03-25 22:21:00 -0600
categories: command
---

- [Minecraft：Java 版命令返回值列表。](#minecraftjava-版命令返回值列表)
- [正文](#正文)
	- [advancement](#advancement)
		- [grant](#grant)
		- [revoke](#revoke)
	- [bossbar](#bossbar)
		- [add](#add)
		- [get](#get)
		- [list](#list)
		- [remove](#remove)
		- [set](#set)
	- [clear](#clear)
	- [clone](#clone)
	- [data](#data)
		- [get](#get-1)
		- [merge](#merge)
		- [modify](#modify)
		- [remove](#remove-1)
	- [datapack](#datapack)
		- [disable](#disable)
		- [enable](#enable)
		- [list](#list-1)
	- [debug](#debug)
		- [start](#start)
		- [stop](#stop)
	- [defaultgamemode](#defaultgamemode)
	- [difficulty](#difficulty)
	- [effect](#effect)
		- [give](#give)
		- [clear](#clear-1)
	- [enchant](#enchant)
	- [execute](#execute)
	- [experience](#experience)
		- [add](#add-1)
		- [query](#query)
		- [set](#set-1)
	- [fill](#fill)
	- [forceload](#forceload)
		- [add](#add-2)
		- [query](#query-1)
		- [remove](#remove-2)
	- [function](#function)
	- [gamemode](#gamemode)
	- [gamerule](#gamerule)
	- [give](#give-1)
	- [help](#help)
	- [kick](#kick)
	- [kill](#kill)
	- [list](#list-2)
	- [loot](#loot)
	- [locate](#locate)
	- [me](#me)
	- [msg](#msg)
	- [particle](#particle)
	- [playsound](#playsound)
	- [publish](#publish)
	- [recipe](#recipe)
	- [reload](#reload)
	- [replaceitem](#replaceitem)
	- [say](#say)
	- [schedule](#schedule)
	- [scoreboard](#scoreboard)
		- [objectives add](#objectives-add)
		- [objectives list](#objectives-list)
		- [objectives modify](#objectives-modify)
		- [objectives remove](#objectives-remove)
		- [objectives setdisplay](#objectives-setdisplay)
		- [players add](#players-add)
		- [players enable](#players-enable)
		- [players get](#players-get)
		- [players list](#players-list)
		- [players operation](#players-operation)
		- [players remove](#players-remove)
		- [players reset](#players-reset)
		- [players set](#players-set)
	- [seed](#seed)
	- [setblock](#setblock)
	- [setworldspawn](#setworldspawn)
	- [spawnpoint](#spawnpoint)
	- [spreadplayers](#spreadplayers)
	- [stopsound](#stopsound)
	- [summon](#summon)
	- [tag](#tag)
		- [add](#add-3)
		- [list](#list-3)
		- [remove](#remove-3)
	- [team](#team)
		- [add](#add-4)
		- [empty](#empty)
		- [join](#join)
		- [leave](#leave)
		- [list](#list-4)
		- [modify](#modify-1)
		- [remove](#remove-4)
	- [teleport](#teleport)
	- [tell](#tell)
	- [tellraw](#tellraw)
	- [time](#time)
		- [add](#add-5)
		- [query day](#query-day)
		- [query daytime](#query-daytime)
		- [query gametime](#query-gametime)
		- [set](#set-2)
	- [title](#title)
		- [actionbar](#actionbar)
		- [clear](#clear-2)
		- [reset](#reset)
		- [subtitle](#subtitle)
		- [times](#times)
		- [title](#title-1)
	- [tp](#tp)
	- [trigger](#trigger)
	- [w](#w)
	- [weather](#weather)
	- [worldborder](#worldborder)
		- [add](#add-6)
		- [center](#center)
		- [damage](#damage)
		- [get](#get-2)
		- [set](#set-3)
		- [warning distance](#warning-distance)
		- [warning time](#warning-time)
	- [xp](#xp)

# Minecraft：Java 版命令返回值列表。

本文最后更新于：1.14.4

使用 Ctrl + F 可以快速找到你需要的命令。

由于 Minecraft Wiki 上的相关命令页面已经包含了命令的结果，本文将不再加入 1.14.4 后新加入命令的数据。

# 正文

**命令返回值**，直观来看是命令在 `execute store result ... run ...` 命令中可被存储的值。  \
该值为 `Int32` 类型，取值范围从 `-2,147,483,648` 到 `2,147,483,647`，因此有部分命令的返回值会发生溢出，本文会对有可能溢出的命令进行标记。

## advancement
### grant

返回：实际给予的进度的个数。
如果玩家被给予某个已经达成的进度，该进度不会被算入返回值。
特别地，当实际给予的进度数量为 `0` 时，没有返回值（即 `execute store` 命令不会引起任何改变）。

### revoke

返回：实际剥夺的进度的个数。
如果玩家被给予某个已经达成的进度，该进度不会被算入返回值。
特别地，当实际剥夺的进度数量为 `0` 时，没有返回值（即 `execute store` 命令不会引起任何改变）。

## bossbar
### add

返回：在命令执行以后，存在的自定义 bossbar 的数量。
由游戏创建的 bossbar（如末影龙的血条）不会被计入。
特别地，如果尝试创建了一个已经存在的 bossbar，返回 `0`。

### get

| 参数 | 返回值 |
|-|-|
| max | 该 bossbar 的最大值。 |
| players | 可以见到该 bossbar 的玩家个数（也许会溢出，本人没有那么多玩家进行测试，相信你们也没有）。 |
| value | 该 bossbar 的值。 |
| visible | 若该 bossbar 可见，则返回 1；否则返回 `0`。 |

### list

返回：存在的自定义 bossbar 的数量。
由游戏创建的 bossbar（如末影龙的血条）不会被计入。

### remove

返回：在命令执行以后，存在的自定义 bossbar 的数量。
由游戏创建的 bossbar（如末影龙的血条）不会被计入。
特别地，如果尝试删除了一个不存在的 bossbar，返回 `0`。

### set

| 参数 | 返回值 |
|-|-|
| color | 永远的 `0`。 |
| max | 修改后的 bossbar 的最大值。特别地，如果修改后的值与原先值相同，返回 0。 |
| name | 永远的 `0`。 |
| players | 修改后的可以见到 bossbar 的玩家个数。特别地，如果修改后的**玩家**与原先**玩家**相同，返回 `0`。 |
| style | 永远的 `0`。 |
| value | 修改后的 bossbar 的值。特别地，如果修改后的值与原先值相同，返回 `0`。 |
| visible | 永远的 `0`。 |

## clear
返回：实际清除的物品个数。如果最大数量指定为 `0`，将会返回背包中指定物品的总个数。
## clone
返回：被复制的方块个数。

| 模式 | 返回值 |
|-|-|
| replace | 该区域包含的所有方块的个数 |
| masked | 该区域包含的非空气方块的个数 |
| filtered | 该区域包含的满足指定条件的方块的个数 |

特别地，当复制失败（非 force 模式且区域重叠），返回 `0`。
## data
### get

当指定的方块没有 NBT 时，返回 `0`。

**当指定的为实体/存储/方块实体时**

下表为乘上倍数（scale）前的数据。

| 路径 | 返回值 |
|-|-|
| 未指定 | 永远为 1 |
| Compound | 该 Compound 包含的 键-值对 个数。特别地，对于根 Compound，返回值是`0`（可能溢出） |
| List | 该 列表 包含的 项 个数（可能溢出） |
| Byte/Int/:ong Array | 该 数组 包含的 项 个数（可能溢出） |
| String | 该 字符串 包含的 字符 个数，其中转义字符算上转义符号为一位（即`\\` `\"`的位数是`1`），中文字符的位数是`1`（可能溢出） |
| Byte Short Int | 该 数字 的值 |
| Long | 该 数字 的值（极有可能溢出） |
| Float Double | 该 数字 直接舍弃小数位的值（可能溢出） |

### merge

当指定的 NBT 与原先 NBT 不同，返回 `1`；
当指定的 NBT 与原先 NBT 完全相同时，返回 `0`。

### modify

当成功编辑时，返回 `1`；
当编辑失败，或是编辑后的值和之前完全一致时，返回 `0`。

### remove

当尝试移除不存在的路径，返回 `0`；
当移除存在的路径，返回 `1`。
## datapack
### disable

返回：禁用掉指定的数据包后仍然启用的数据包个数。
特别地，当尝试禁用不存在的数据包或已经禁用的数据包，返回 `0`。

### enable

返回：命令执行后启用的数据包个数。
特别地，当尝试启用不存在的数据包或已经启用的数据包，返回 `0`。

### list

返回：命令指定类型（`available` 或 `enabled`）的数据包的个数。
## debug
### start

返回：`0`。

### stop

返回：自 `debug start` 后到现在的 tps（ticks per second）（直接舍弃末位小数）。
特别地，如果没有执行过 `debug start`，返回 `0`。
## defaultgamemode
返回：`0`。
## difficulty
若在参数中指定了难度，返回 `0`；
若没有指定参数，返回当前难度的数字 ID，下表是一个对应关系。

| 难度 | 英文ID | 数字ID |
|-|-|-|
| 和平 | peaceful | 0 |
| 简单 | easy | 1 |
| 普通 | normal | 2 |
| 困难 | hard | 3 |

## effect
### give

返回：实际被给予效果的实体个数。
例如，即使指定了给 2 个实体效果，但其中有 1 个实体不支持状态效果，返回 `1` 而不是 `2`。

### clear 
返回：实际被清除效果的实体个数。
例如，即使指定清除 2 个实体的效果，但其中有 1 个实体没有这个效果或不支持状态效果，返回 `1` 而不是 `2`。
## enchant
返回：实际的手中物品被给予附魔魔咒的实体个数。
例如，即使指定给予 2 个实体手中物品附魔魔咒，但其中有 1 个实体手中没有物品、手中物品已附魔或手中物品不支持附魔，返回 `1` 而不是 `2`。
## execute
若没有接 `run`，且没有 `if|unless`，没有返回值（即 `execute store` 命令不会引起任何改变）；
若没有接 `run` 但有 `if|unless`，按下表返回：  

| 子命令 | 返回值 |
|-|-|
| block | 若方块匹配，返回 `1`；否则返回 `0`。 |
| blocks | 若方块匹配，`all` 模式返回原区域方块个数，`masked` 模式返回原区域非空气方块个数；否则返回 `0`。 |
| data | 返回按照指定的 NBT 路径能够在指定实体/存储/方块实体上获得的 NBT 标签的个数。 |
| entity | 返回匹配的实体个数。 |
| score | 若分数匹配，返回 `1`；否则返回 `0`。 |

若 `run` 后命令在该 `execute` 指定的命令执行者（们）执行后，每个执行者得到的返回值相同，则返回该返回值；若任一返回值不同，则返回 `0`。
## experience
### add

返回：被加（或减）经验的玩家的个数。

### query

返回：指定玩家的经验等级/经验点数。
注意：点数为在当前等级下的点数，并非玩家的全部点数。

### set

返回：被设置经验的玩家的个数。 特别地，当设定的经验点数大于玩家当前等级能容纳的最大点数时，返回 `0`。
## fill
返回：实际被填充的方块的个数。
在非 `destroy` 模式下，指定区域内与指定方块相同的方块不会被算入个数中；
在 `destroy` 模式下，返回值即为指定区域内的方块数量。特别地，在空气中填充空气，即使是 `destroy` 模式也不会被计入，这一点和 [setblock](#setblock) 命令不同。
## forceload
### add

返回：命令执行后新增的强制加载区块的个数。

### query

若指定 `<pos>` 参数，当指定坐标所在的区块已被强制加载时，返回 `1`，否则返回 `0`。
若没有指定 `<pos>` 参数，则返回当前世界中被强制加载的区块的个数。

### remove

若指定的参数为 `all` 时，永远返回 `0`。
否则，返回命令执行后减少的强制加载区块的数量。
## function
返回：执行该函数后聊天栏显示的“已执行命令个数”。
（事实上，没人知道这个数字是使用怎样弱智的手法计算出来的。在函数递归、互相调用的情况下，这个返回的数字简直令人作呕。作为普通玩家，我们也不需要知道这些没用的东西。就让 MJ 自己 S[size=0px]*B 去吧！）
## gamemode
返回：实际被改变模式的玩家个数。
如果某个玩家本身就是指定模式，它不会被算入返回值。
## gamerule
当不指定值（即查询指定规则的值）时，按下表返回该规则的值。 当指定值（即设置制定规则的值）时，按下表返回你指定的值。

| 规则类型 | 返回值 |
|-|-|
| Boolean | `true` 返回 `1`，`false` 返回 `0`。 |
| Int | 返回该数字的值 |

## give
返回：被给予物品的玩家个数。
## help
返回：手动执行该命令后，输出的内容行数。
## kick
返回：被踢出的玩家数量。
## kill
返回：被杀死的实体个数。
## list
返回：在线的玩家个数。
## loot
返回：掉落的物品种数。

e.g. 掉落了「1 个骨头」或「2 个骨头」，返回值均为 `1`；掉落了「2 个骨头和 3 支箭」，返回值则为 `2`。
## locate
返回：当前坐标距离指定结构坐标的水平距离。 特别地，当指定结构不存在，返回 `0`。
## me
返回：`1`。
## msg
返回：被私信的玩家个数。
## particle
返回：`1`。
## playsound
返回：被播放音乐的玩家个数。
## publish
返回：该局域网世界被分配的端口数。 特别地，如果该世界已经被开向局域网，或尝试在服务器内执行该命令，返回 `0`。
## recipe
返回：实际解锁/剥夺的配方个数。
## reload
返回：`0`。
## replaceitem
返回：被替换物品的实体/方块个数。
## say
返回：`1`。
## schedule
返回：函数被计划执行的游戏时间（即手动执行命令时，提示「即游戏时间 xxx 时执行」的「xxx」）。
## scoreboard
### objectives add

返回：命令执行后的计分项个数。 特别地，当尝试创建一个已经存在的计分项时，返回 `0`。

### objectives list

返回：当前计分项个数。

### objectives modify

返回：`0`。

### objectives remove

返回：命令执行后的计分项个数。 特别地，当尝试移除一个并不存在的计分项时，返回 `0`。

### objectives setdisplay

返回：`0`。

### players add

返回：命令执行后，指定目标指定计分项的分数。 特别地，当尝试为不存在的计分项添加分数时，返回 `0`。

### players enable

返回：被激活指定计分项的目标个数。 特别地，当尝试激活非 trigger 计分项时，返回 `0`。

### players get

返回：指定目标指定计分项的分数。 特别地，当尝试获取不存在的计分项的分数时，返回 `0`。

### players list

返回：指定目标所拥有的分数个数。

### players operation

返回：运算结束后，第一组参数指定的目标在指定计分项上的分数。

### players remove

没有返回值（即 `execute store` 命令不会引起任何改变）。

### players reset

返回：被重置的目标个数。

### players set

返回：命令执行后，指定目标指定计分项的分数。
## seed
返回：当前地图的种子。（极有可能溢出）
## setblock
返回：实际放置的方块个数。
在非 `destroy` 模式下，原位置的方块与放置的方块不同时，返回 `1`，否则返回 `0`。
在 `destroy` 模式下，永远返回 `1`，这一点和 [fill](#fill) 命令不同，请注意。
## setworldspawn
返回：`1`。
## spawnpoint
返回：被设置出生点的玩家个数。
## spreadplayers
返回：被分散的实体个数。
## stopsound
返回：被停止音效的玩家个数。
## summon
返回：如果召唤成功，返回 `1`；否则返回 `0`。
## tag
### add

返回：实际被加上 tag 的实体个数。
如果某个实体已经有了该 tag，则返回 `0`。

### list

返回：指定实体的 tag 个数。

### remove

返回：实际被移除 tag 的实体个数。
如果某个实体并没有该 tag，则返回 `0`。
## team
### add

返回：命令执行后，存在的队伍个数。 特别地，如果队伍已经存在，则返回 `0`。

### empty

返回：从指定队伍中移出的实体个数。

### join

返回：新加入指定队伍的实体个数。
即使该实体已经在指定队伍内，也会被计入。

### leave

返回：退出队伍的实体个数。
即使该实体没有参加任何队伍，也会被计入。

### list

返回：存在的队伍个数。

### modify

返回：`0`。

### remove

返回：命令执行后，存在的队伍个数。
 特别地，如果指定队伍并不存在，则返回 `0`。
## teleport
返回：被传送的实体个数。
## tell
参见 [msg 命令](#msg)。
## tellraw
返回：被显示文本的玩家个数。
## time
### add

返回：命令执行后的 Minecraft 中自破晓后的时间（单位：刻）。

### query day

返回：Minecraft 中度过的游戏内天数（单位：天）。

### query daytime

返回：Minecraft 中自破晓后的时间（单位：刻）。

### query gametime

返回：玩家游玩 当前 Minecraft 存档的总时长（单位：刻）。

### set

返回：命令执行后的 Minecraft 中自破晓后的时间（单位：刻）。

## title
### actionbar

返回：被设置 actionbar 的玩家个数。

### clear

返回：被清除标题的玩家个数。

### reset

返回：被重置数据的玩家个数。

### subtitle

返回：被设置副标题的玩家个数。

### times

返回：被设置时间的玩家个数。

### title

返回：被标题的玩家个数。
## tp
参见 [teleport 命令](#teleport)。
## trigger
返回：在命令执行以后，指定计分项在当前目标上的分数。 特别地，当指定目标没有权限修改指定计分项时，返回 `0`。
## w
参见 [msg 命令](#msg)。
## weather
返回：指定天气状态的持续时间（单位为刻，命令中的参数单位为秒）。
## worldborder
### add

返回：世界边界变化的宽度（正数为增加，负数为减小）。

### center

返回：`0`。

### damage

返回：命令中设定的伤害的值。
特别地，如果伤害值没有任何改变，返回 `0`。

### get

返回：世界边界的宽度。

### set

返回：世界边界变化的宽度（正数为增加，负数为减小）。

### warning distance

返回：开始警告的距离。

### warning time

返回：开始警告的时间。
## xp
参见 [experience 命令](#experience)。
