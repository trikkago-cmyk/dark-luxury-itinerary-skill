[English](./README.en.md)

![Dark Luxury Itinerary Skill Hero](./assets/screenshots/hero-desktop.png)

# Dark Luxury Itinerary Skill

你有没有也遇到过这样的时刻？

明明已经把一趟旅行的路线、餐厅、住宿、注意事项都整理好了，发出去却还是像一页被匆忙导出的文档。信息是全的，心情却不见了。

又或者，你脑子里已经有了“从哪到哪、几天几夜、预算大概多少”，但一想到还要做路书规划，就先累了一半。

如果你也有过这种瞬间，这个 skill 就是为你准备的。

它会把“旅行需求 / 现成路书 / 第一人称游记”，直接做成一个真正值得分享的旅行网页。

一句话说：你负责告诉它想去哪里，它负责把这趟旅程做成一个体面、好看、设计感满满，还能直接分享出去的小站。

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

不管你用哪个 App，最快的方式其实都差不多：

1. 打开 `dark-luxury-itinerary-skill/SKILL.md`
2. 把里面的核心说明放进你当前工具的项目规则、系统提示，或自定义 agent 里
3. 直接输入你的旅行需求，让它开始生成

比如你可以直接这样说：

> 帮我做一个从武汉到襄阳的两天一夜旅行路书网页，移动端优先，保留高级杂志感，自动补图并配置一首舒缓的背景音乐。

如果你的工具支持直接导入 skill 包，也可以直接使用：

- `dist/dark-luxury-itinerary-skill.skill`

## 仓库里有什么？

- `dark-luxury-itinerary-skill/`
  完整 skill 源目录

- `dark-luxury-itinerary-skill/SKILL.md`
  核心工作流、硬规则、视觉系统与 QA 规范

- `dark-luxury-itinerary-skill/references/`
  benchmark、行程规划、文风约束、实现配方、媒体素材工作流

- `dist/dark-luxury-itinerary-skill.skill`
  打包好的可安装 `.skill` 文件


## 仓库结构

```text
.
├── assets/
│   └── screenshots/
├── dark-luxury-itinerary-skill/
│   ├── SKILL.md
│   ├── agents/
│   └── references/
└── dist/
    └── dark-luxury-itinerary-skill.skill
```

## 当前版本

- `v1.0.0`
