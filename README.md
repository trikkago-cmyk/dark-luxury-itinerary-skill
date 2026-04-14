[English](./README.en.md)

![Dark Luxury Itinerary Skill Hero](./assets/screenshots/hero-desktop.png)

# Dark Luxury Itinerary Skill

你有没有也遇到过这样的时刻？

明明已经把一趟旅行的路线、餐厅、住宿、注意事项都整理好了，发出去却还是像一页被匆忙导出的文档。信息是全的，心情却不见了。

又或者，你脑子里已经有了“从哪到哪、几天几夜、预算大概多少”，但一想到还要做路书规划，就先累了一半。

如果你也有过这种瞬间，这个 skill 就是为你准备的。

它会把“旅行需求 / 现成路书 / 第一人称游记”，直接做成一个真正值得分享的旅行网页。

一句话说：你负责告诉它想去哪里，它负责把这趟旅程做成一个体面、好看、j味满满，还能直接分享出去的小站。

它最讨人喜欢的地方其实很简单：

- 极致傻瓜：只需输入旅行需求，就能一站式生成路书和网页
- 极致优雅：高级杂志视觉，几乎没有 AI UI 味，还可以配上氛围型背景音乐

先看看它做出来大概是什么样子。

## 真实产出

下面这些都是真实项目，不是临时做来截图的展示稿。

<table>
  <tr>
    <td align="center">
      <a href="https://dark-luxury-travel-itinerary.vercel.app">
        <img src="./assets/screenshots/xishuangbanna-hero-mobile.png" alt="Xishuangbanna route guide mobile screenshot" width="220" />
      </a>
      <br />
      <strong>Xishuangbanna Route Guide</strong>
      <br />
      抚仙湖 · 西双版纳路书
    </td>
    <td align="center">
      <a href="https://wuhan-jingshan-travel-guide.vercel.app">
        <img src="./assets/screenshots/jingshan-route-mobile.png" alt="Jingshan route guide mobile screenshot" width="220" />
      </a>
      <br />
      <strong>Jingshan Route Guide</strong>
      <br />
      武汉 · 京山路书
    </td>
  </tr>
  <tr>
    <td align="center">
      <a href="https://youji.travel-itinerary-jingshan.online">
        <img src="./assets/screenshots/jingshan-memoir-mobile.png" alt="Jingshan memoir mobile screenshot" width="220" />
      </a>
      <br />
      <strong>Jingshan Memoir</strong>
      <br />
      京山四日三夜游记
    </td>
    <td align="center">
      <a href="https://skill-solid-coldstart-routeguide-ag.vercel.app">
        <img src="./assets/screenshots/coldstart-hangzhou-mobile.png" alt="Cold-start Hangzhou route guide mobile screenshot" width="220" />
      </a>
      <br />
      <strong>Cold-start Validation</strong>
      <br />
      杭州两天一夜冷启动测试站
    </td>
  </tr>
</table>

如果你做过旅行计划，或者替别人整理过路线，你大概会很懂这些小崩溃：

- 行程已经写完了，但发出去不过是一篇难读的文档
- 想把它做得高级一点，结果时间全花在找图、调排版上
- 只想做一份家人看得懂、客户愿意读的路线页，却越做越像模板
- 每次换一个目的地，都要把同样的结构、提示、配图逻辑再重来一遍

这个 skill 干的，就是把这些重复又耗人的事情一起接住。

它会先帮你把路书结构、页面节奏、图片氛围、标签语义和音乐交互理顺，再把它们落成一个真正可用的旅行站点。

所以它会特别适合这些人：

- 家庭旅行计划：想把一次出行安排得清楚、体面，又不想折腾一整套设计和前端
- 个体旅行社、小型工作室：想把路线、体验亮点和整体气质做成一个更有说服力的展示页
- 有游记、攻略、朋友圈长文的人：想把内容从“能看”升级到“值得分享”

## 怎么开始

好消息是，大多数时候你根本不需要先研究 `.skill` 包怎么装。

如果你只是想最快开始，最简单的做法是：把这套规则接到你正在用的 agent 里，然后直接说一句像这样的话：

> 帮我做一个从武汉到襄阳的两天一夜旅行路书网页，移动端优先，保留高级杂志感，自动补图并配置一首舒缓的背景音乐。

下面是几种最实用的接入方式。

### Cursor

如果你用的是 Cursor，最省事的方式其实不是装包，而是直接把规则放进项目里。

- 简单版：把精简后的说明放进项目根目录 `AGENTS.md`
- 规则版：放进 `.cursor/rules/`，做成一个可复用的 `.mdc` 规则
- CLI 版：`cursor-agent` 会读取同一套 `.cursor/rules`，也会读取项目根的 `AGENTS.md` 和 `CLAUDE.md`

换句话说，你在 Cursor IDE 里能用的那份规则，通常在 Cursor CLI 里也能继续用。

### Claude Code

Claude Code 不必等“原生 skill 安装”。

- 最简单：把核心说明写进项目里的 `CLAUDE.md`
- 更顺手：新建 `.claude/commands/travel-web.md`，之后在会话里直接输入 `/travel-web`
- 如果你想团队共用，就把 `CLAUDE.md` 和 `.claude/commands/` 一起放进仓库

这样你就不用每次都重复打一大段提示词了。

### OpenCode

OpenCode 更适合把这套能力做成一个专用 agent。

- 在项目里创建 `.opencode/agents/travel-web.md`
- 把这套旅行网页的核心 prompt 放进去
- 在会话里用 `@travel-web` 直接调用

如果你希望它跟着项目走，这种方式会非常轻。

### OpenClaw

OpenClaw 是最接近“原生 skill”这条路的。

- 直接把 `dark-luxury-editorial-web-skill/` 复制到 `<workspace>/skills/`
- 或者放到 `~/.openclaw/skills/`，让本机所有项目共享
- 如果你只是想分发或备份，再使用 `dist/dark-luxury-editorial-web-skill.skill`

也就是说，对 OpenClaw 来说，真正的“本体”是 skill 文件夹本身，`.skill` 更像打包产物。

### 如果你只想复制就用

那最直接的入口就是这个源文件：

- `dark-luxury-editorial-web-skill/SKILL.md`

你完全可以把它当作母版，按你正在使用的工具，拆进 `AGENTS.md`、`CLAUDE.md`、`.cursor/rules/`、`.opencode/agents/` 或 OpenClaw 的 `skills/` 目录里。

## 仓库里有什么？

- `dark-luxury-editorial-web-skill/`
  完整 skill 源目录

- `dark-luxury-editorial-web-skill/SKILL.md`
  核心工作流、硬规则、视觉系统与 QA 规范

- `dark-luxury-editorial-web-skill/references/`
  benchmark、行程规划、文风约束、实现配方、媒体素材工作流

- `dist/dark-luxury-editorial-web-skill.skill`
  打包好的可安装 `.skill` 文件

## 最常见的使用方式

1. 直接安装 `.skill` 文件，用它跑新的旅行网页项目
2. 把仓库里的 `SKILL.md + references/` 当作你自己的 SOP 基线
3. 用它去校准你的 travel-web agent，让它别再把路书做成模板站

## 安装文件

- `dist/dark-luxury-editorial-web-skill.skill`

## 仓库结构

```text
.
├── assets/
│   └── screenshots/
├── dark-luxury-editorial-web-skill/
│   ├── SKILL.md
│   ├── agents/
│   └── references/
└── dist/
    └── dark-luxury-editorial-web-skill.skill
```

## 当前版本

- `v1.0.0`
