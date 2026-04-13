[English](./README.en.md)

# Dark Luxury Editorial Web Skill

不是把攻略贴进网页。  
是把一份旅行材料，做成一个真的有人愿意点开、滑完、听完、再转发出去的旅行小站。

它专门处理一种很常见也很恼人的情况：  
内容其实不错，审美也有，但一交给通用生成工具，最后就变成黑底、几段字、几张不对味的图，首屏和次页像硬拼起来的两块板。

## 它解决什么问题？

如果你做过旅行网页，大概率踩过这些坑：

- 文案有了，页面却没有封面感
- 首屏和次页有明显切线，一下滑就出戏
- 标签、配图、时间轴都在，但语义不准，越看越像模板
- 移动端一打开就露馅，字太细、层级太乱、视觉重心不稳
- 音乐、素材 sourcing、字体体积这些问题总在最后一刻爆雷

这个 skill 不是“再生成一个页面”。  
它是把这些最容易返工的地方，提前变成规则和工作流。

## 哪些场景特别适合用它？

### 1. 你已经有攻略了，只差一个体面的网页

比如你手里已经有：

- 飞书文档
- Notion 页面
- Word / DOCX
- 聊天记录整理出来的行程

你不想只是“转网页”，你真正想要的是：

- 有封面感的首页
- 和次页自然融合的过渡
- 每天路线清楚，但不死板、不像旅游模板
- 发出去别人会觉得“这个站做得真好”

### 2. 你只有一个旅行意图，还没有成型路书

比如你只知道：

- 从哪里去哪里
- 几天几夜
- 想要什么风格
- 大概预算

这时候它不只是网页生成器，也是一套路书工作流。  
它会先把路线、节奏、模块和信息结构补完整，再做成页面。

### 3. 你有一篇游记，不想被 AI 改得没了语气

很多工具会把第一人称游记改成一篇“写得很工整，但完全不像你”的总结。  
这套 skill 会明确区分“路书模式”和“游记模式”，尽量保留原来的口吻，只帮你把结构和节奏理顺。

### 4. 你已经有个半成品网页，但总觉得差一口气

它特别适合修这些老毛病：

- 首屏和次页割裂
- 时间轴做得太卡、太重、太花
- 标题不居中，视觉重心不稳
- 标签和配图语义不对
- 音乐播放器看起来像外挂组件
- 字体一加就把包体积炸大

## 它具体会怎么帮你？

它的工作方式很简单，但很有效：

1. 先判断你给的是旅行意图、路书，还是第一人称游记
2. 先整理结构，再做视觉：Hero、每日安排、时间节点、地点 / 食物标签、交通住宿、预算模块都会先被理顺
3. 先写 shot list，再找图、落图、配氛围，确保页面不是“最后才想起要补图”
4. 最后统一检查那些最容易翻车的细节：首屏过渡、时间轴节点、标签语义、音乐状态、移动端层级、字体体积

## 你可以怎么用？

- 丢给它一份飞书 / Notion / Word / 聊天整理稿，让它直接做成旅行网页
- 只给“从哪里到哪里、几天几夜、什么气质、多少预算”，让它先补完整套路书再出网页
- 拿它去修你已经做了一半、但总不够高级的旅行站
- 把它当成你自己的 travel-web agent 基线，后面每个目的地都能复用

## 为什么它比普通网页生成更靠谱？

因为它不是只会说“做一个高级页面”。  
它把真实项目里反复踩过的坑，写成了明确的执行规则。

换句话说，它更像一个已经做过几轮实战的 travel-web 制作人，而不是一个只会给你吐一版模板的页面生成器。

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
