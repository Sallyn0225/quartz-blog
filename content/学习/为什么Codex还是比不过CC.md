---
title: 为什么Codex还是比不过CC
description: 最近没有用多模型协作，也没有用最聪明的opus，只用codex尝试完成全栈开发的任务，但是最终还是破防了——特别是在前端上。
tags:
- 折腾大王
- 开发
- codex
date: 2026-03-29
draft: false
---

## 为什么GPT的前端如此糟糕

原视频：https://www.youtube.com/watch?v=l-gfVIm0Xn8

B站中字：https://www.bilibili.com/video/BV1ehXbBuEoc/

---

> [!note] 以下内容为我边看边记录 无AI润色 可能看着会有些口水话

theo指出openAI近期发的那篇关于GPT-5.4在前端上有明显进步的文章特别搞笑。~~刚好这几天我的any牌路由器彻底断供了~~，反重力和cli还没死但是不敢反代。所以我的前端全部都是用GPT+他们官方的skill做的，只能说是非常灾难。

![[为什么GPT的前端如此糟糕-20260329_17-07-45.webp]]

甚至在博客中openAI给出的示例都有问题。~~但是在这里我主要想吐槽关于这个页面风格~~，在使用了skill之后，注意到GPT好像总喜欢在左上角用个巨大无比的衬线体标题，然后加上各种各样的卡片框住元素，以及自行添加很多完全不需要添加的说明文字。

theo不推荐使用openAI的前端技能，而是使用vercel官方出的那个 [skills.sh](https://skills.sh/) 这个东西有个自动发现skills的skill，之前在[linuxdo站内的帖子](https://linux.do/t/topic/1797384/11?u=sallyn)里看到过，不过我自己还没有装上去。

![[为什么GPT的前端如此糟糕-20260329_17-08-42.webp]]

另外他还提了一个很有意思的网站，对比不同的模型，在使用skill前后做出来的网站：https://ui-design-bench.vercel.app/ 这个可以点进去看看

![[为什么GPT的前端如此糟糕-20260329_17-09-02.webp]]

theo对着不用skill的kimi k2.5一顿夸

![[为什么GPT的前端如此糟糕-20260329_17-09-13.webp]]

后面来到对比加上了skill的页面。theo指出它没有对GPT模型使用openAI提供的技能，**指出甚至这个skill的效果比anthropic的更差**。

GPT-5.4 真是卡片大王，上了skill还在做一堆的卡片，所有风格都是卡片，卡片里面还在套卡片。

![[为什么GPT的前端如此糟糕-20260329_17-09-29.webp]]

他们自己的skill甚至要求使用无卡片布局，但是没有什么用，**GPT在他们这个博客中的案例依旧在使用卡片**，而且他们还拿了出来。而且 "cards" 这个词在他们的skill中出现了13次，但是模型就是不遵守。

![[为什么GPT的前端如此糟糕-20260329_17-09-45.webp]]

最搞笑的是，这个箭头展开的时候应该是往下的，但是它压根没往下！theo不说我都没注意到这个点🤣GPT的前端真的是史啊

> [!attention] 另外，如果你在用A\的前端skill，可以移除这一行

Tone里有一个 `retro-futuristic`，把这个给移除了。

### 问题究竟出在哪

theo认为是gpt模型在强化学习上出了问题。训练模型需要有一个“好”的参考标准，或许是因为他们找的参考并没有那么好——比如说包含了一堆卡片的一个网页。另外就是GPT的“模板味”很重，打个比方就是

- GPT大概只有4种设计风格
- Opus可能有个10种，但是有少数很糟糕。
- Gemini的数量很多，但是同样糟糕的设计也更多，更要命的是gemini不听指令。

![[为什么GPT的前端如此糟糕-20260329_17-10-50.webp]]

Theo自己在写前端用的最多的模型还是opus，但也指出opus也有自己的怪癖，比如说特别喜欢加入各种药丸/使用很丑的字体/裁剪图片错误等等，这个时候他会自己手动进行更改；其次是Gemini，但是很多时候需要抽卡的次数更多，但一旦抽出来想要的，就交给其他模型进行更改；至于GPT，用来修BUG😆

虽然说他自己也是猜想，因为后两家模型在前端的表现上会有很多相似的地方，但是GPT并不是。他认为是openAI用于训练模型前端的数据库并没有一并更新所导致的。Who knows? 反正我确实是已经放弃让GPT帮我写前端了。

## 在windows环境下打不过CC的Codex

除了前端问题，本身Codex的功能性也是不如Claude的。

首先，Claude最近掏出来的杀手锏有点太多了。首先是一个remote-control的功能，但是这个功能因为我没有官方的订阅，所以对我来说是用不上的。

https://code.claude.com/docs/en/remote-control

但是他们后面紧接着就推出了类似龙虾一样，可以在telegram和discord上操作CC的一个插件。

https://code.claude.com/docs/en/channels

这个东西说实话就是我想要的东西。因为龙虾的代码真的就是纯粹的一坨屎山。我不敢在我的主要的服务器或者电脑部署就是怕哪天这人合并代码的时候合并进去一个严重的安全漏洞，那我的服务器/电脑就直接爆了。

> 另外，现在微信和飞书也支持通过类似[cc-connect](https://github.com/chenhg5/cc-connect)这样的项目把各家的coding agent进行接入。所以我完全没有必要安装龙虾。

另外，claude code在agent的设计上还是要比codex好的多的。不知道为什么，codex的plan mode始终没有CC好用，总给人一种设计的精度不深的味道。另外还无法自动进入plan mode进行计划。加上CC的subagent和**agent teams**的设计，Codex这个有时候无法自动回报的subagent是做的真的不太行。

另外Codex的删盘情况百出，本质是因为跑在windows上的是基于powershell的。而模型在训练的时候对powershell的命令语料本身就较少，加上powershell的命令复杂，有的时候一个小小的转义错误就会造成很严重的后果。这点是不如基于git bash的CC的。

要我说如果不是因为opencode也是一个依赖AI开发度高的项目，加上他们经常更新出来一堆BUG，我或许在就用opencode替代codex把GPT模型接进来了。不过这两个cli都可以通过WSL的方式进行使用，在linux环境下就不存在这么多毛病了。**但是说实话我windows原生能用，那我干啥还费劲巴拉去装个WSL**。