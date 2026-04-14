[English](./README.en.md)

![Dark Luxury Editorial Web Hero](./assets/screenshots/hero-desktop.png)

# Dark Luxury Editorial Web Skill

**它是什么？**  
一个“旅行路书生成 + 杂志风网页发布”的一体化 skill。  
一句话卖点：输入旅行需求，就能一键生成精美路书和可分享网页。

**产品截图**

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

## 能解决什么问题？

**场景：我有内容，但做出来不高级**  
解决：把行程结构、配图、标签、音乐和排版一次性拉齐，不再像模板站。

**场景：我只有想法，没有路书**  
解决：输入“从哪到哪、几天几夜、风格、预算”，自动补完整路书再生成网页。

**产品亮点**
- 傻瓜式：只需输入旅行需求，一站式生成路书 + 网页
- 美观：高级杂志视觉，几乎没有 AI UI 味，自带氛围型背景音乐

**适用人群**
- 家庭旅行计划：省心、省时，还保持质感
- 个体旅行社 / 小型工作室：用网页展示路线与体验亮点

## 怎么用？

1. 安装 `dist/dark-luxury-editorial-web-skill.skill`
2. 在 Cursor 里调用该 skill，输入你的旅行需求或现成路书
3. 生成并部署旅行网页

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
