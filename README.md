# 个人游戏demo开发Skill

**Solo Game Demo Development Skill**

中文 · [English](README.en.md)

[![GitHub stars](https://img.shields.io/github/stars/KangarooFighter/solo-game-demo-skill?style=social)](https://github.com/KangarooFighter/solo-game-demo-skill/stargazers) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

**一个人做游戏，让 AI 按职责协作，把想法推进到可玩的 Demo。**

这是一套为 Codex 编写的协作 Skill：把设计、代码、美术和验收分给不同任务，明确谁改哪些文件、什么时候交接、怎样证明做完了。它不是游戏引擎或现成游戏，也不保证“一句话自动生成无 bug 大作”。

## 四个职责，一个可玩的结果

| 职责 | 做什么 |
| --- | --- |
| 01 设计与统筹 | 收敛核心玩法，划定范围，分发任务，整合结果 |
| 02 功能与集成 | 实现玩法、交互、必要的 AI、音效和功能测试 |
| 03 美术与资源 | 制作有统一规格的视觉资源，并给出接入说明 |
| 04 验证与交付 | 检查实际体验与产物，按授权打包、维护版本或发布 |

四个职责不等于每次新建四个窗口。已有任务优先复用，小任务可以合并；没有任务管理工具时，提供可复制的任务单，不假装已经派工。

## 解决哪些协作问题？

- **互相覆盖文件** → 一个共享文件，一个写负责人。
- **大家都在等批准** → 在已有授权内预先约定交接条件。
- **聊天越长，状态越乱** → 一份当前摘要，旧状态单独归档。
- **旧测试通过就发布新版** → 验收结果绑定实际输入版本。
- **每改一点就全量重测** → 按变更和风险验证，保留有效证据。
- **任务都说做完了，Demo 还不能玩** → 以可运行、可操作、可结束、可重玩的完整循环收口。

## 安装

在支持技能安装的 Codex 环境中发送：

```text
使用 $skill-installer 从 https://github.com/KangarooFighter/solo-game-demo-skill
安装 skills/multi-thread-delivery。
```

显示名称是「个人游戏demo开发Skill」；为兼容早期版本，调用名仍为 **`$multi-thread-delivery`**。已有同名本地技能时，先检查差异再更新，不盲目覆盖。

也可以把本仓库的 `skills/multi-thread-delivery/` 放入所用客户端的个人技能目录。不要把它混进游戏源码根目录。技能的发现方式依客户端而异，参见[官方技能说明](https://learn.chatgpt.com/docs/build-skills)；这不是官方精选技能或已上架插件。

## 开始第一个 Demo

```text
使用 $multi-thread-delivery 帮我开发一个游戏 Demo。

项目位置：填写你的项目目录
核心玩法：用两三句话描述玩家做什么、乐趣是什么
目标平台：例如 Mac 键鼠
引擎：例如 Godot；沿用已有工程的版本
首版必须包含：一个完整循环、必要的对手、反馈、结算和重试
本轮不做：例如联网、账号和复杂成长系统

当前对话负责设计与统筹。请创建其余三个独立任务，
分别负责功能与集成、美术资源、验证与交付；已有对应任务则复用。
先明确文件归属、接口和验收，再并行推进。
保持项目现有目录结构；安装、推送和公开发布另按我的明确授权执行。
```

只要设计方案时，直接写“只做设计，不创建任务、不修改文件”。继续迭代时写“复用已有任务，不新建窗口”，再说明新需求和必须保留的规则。

## 中文与英文都可用

Skill 按用户语言加载一份流程，不把两种全文同时塞入上下文。包含协作流程、任务单、工具适配与游戏 Demo 专用参考的完整中英版本。Godot 是示例，不绑定引擎、模型或特定美术风格。

入口：[SKILL.md](skills/multi-thread-delivery/SKILL.md) · [中文游戏流程](skills/multi-thread-delivery/references/game-demo.zh-CN.md) · [English game workflow](skills/multi-thread-delivery/references/game-demo.en.md)

## 能力边界

需要能够读写目标项目、运行相应引擎的 AI 编程环境。多任务、子代理、图像生成、Git 和定时跟进取决于宿主工具及授权；Skill 不会凭空增加这些能力，不会自动购买工具或承诺关机后继续工作。

规则测试、合成输入、导出应用测试和真人体验应分别报告。截图不能证明声音好听，绿色计数也不能证明没有运行错误。具体项目仍需实际试玩与判断。

这个流程提炼自个人游戏原型的多轮协作，并经过独立情境演练；不是跨所有引擎、客户端和项目的成功率基准。本仓库只分享流程，不包含原游戏源码、素材、私人路径或聊天记录。

## 一起改进

欢迎在 [Issues](https://github.com/KangarooFighter/solo-game-demo-skill/issues) 分享卡住的交接、失效的提示或实际项目经验。请说明环境、预期、实际行为和最小复现，删除密钥、私人路径与未公开素材。如果它帮你做出了第一个可玩的 Demo，欢迎点个 Star。

[MIT License](LICENSE) · Copyright 2026 Brian Zhang (KangarooFighter)
