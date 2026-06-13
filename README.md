# Mag[i] — 自然语义搜索引擎

> 一个仿 [Magi](https://magi.com/) 风格的自然语义搜索引擎前端原型。
> 通过实体识别、知识抽取和多源比对,把搜索结果以结构化卡片呈现,而不是传统链接列表。

![status](https://img.shields.io/badge/status-prototype-blue)
![stack](https://img.shields.io/badge/stack-HTML%2FCSS%2FJS-orange)
![lang](https://img.shields.io/badge/UI-%E4%B8%AD%E6%96%87-brightgreen)

---

## ✨ 项目特性

- 🔍 **语义化搜索结果**:将查询目标抽取为"实体",展示描述、属性、标签、近义项
- 🎨 **深 / 浅色双主题**:基于 CSS 变量的完整主题系统,iOS 风格开关切换
- 🏷️ **带源引用**:每个描述短语 / 属性值都标注来源 ID,鼠标悬停时高亮对应来源条目
- ✨ **入场动画**:关键词行依次淡入,SVG 虚线连接线循环流动
- 📐 **响应式布局**:窄屏自动切换为单列,SVG 连线自动隐藏
- 🚀 **零依赖**:纯静态 HTML + CSS + 原生 JS,无需构建工具

---

## 📁 目录结构

```
.
├── home.html      # 首页 —— 搜索入口 + 关注动态 + 关键词胶囊
├── magi.html      # 搜索结果页 —— 实体卡片 + 多源信息
└── README.md      # 本文件
```

---

## 🚀 快速开始

由于是纯静态页面,**无需任何构建步骤**。

### 方式 1:直接打开

```bash
# macOS
open home.html

# Linux
xdg-open home.html

# Windows
start home.html
```

### 方式 2:本地起一个简易服务器(推荐)

```bash
# Python 3
python3 -m http.server 8000

# Node.js (需要全局安装 http-server)
npx http-server -p 8000
```

然后访问 <http://localhost:8000/home.html>

---

## 🧩 页面说明

### 1. 首页 (`home.html`)

- 顶部 Logo:`Mag[i]`(使用 Tenor Sans 衬线字体)
- 中央搜索框:聚焦后输入查询
- 主题切换:iOS 风格开关,深色(默认) / 浅色
- **Magi 正在关注**:实时新闻列表,点击跳转到对应来源
- **从该来源学习到...**:关键词胶囊标签,支持二次检索
- 底部多组关键词小卡片,展示来源关系

### 2. 搜索结果页 (`magi.html`)

以"马云"为示例查询,展示结构化的实体卡片:

| 区块 | 内容 |
| --- | --- |
| 实体标题 | 大字号主体名 + 圆形置信度分数(0-100) |
| 描述 | 多个引号短语,带绿色下划线标识,颜色编码代表来源数量 |
| 属性 | 两列网格 `key → value` 卡片,支持展开 |
| 标签 | 实心圆角 chip,按来源充分度分级 |
| 近义项 | 别名 / 俗称 / 译名 |
| 主要学习来源 | 右侧文章列表,hover 描述词时高亮对应来源 |

#### 交互细节

- **悬停高亮**:鼠标悬停描述短语时,右侧对应的来源条目获得蓝色边框高亮
- **入场动画**:描述 / 属性 / 标签依次淡入
- **SVG 连线**:描述短语与对应来源之间绘制流动虚线,营造"知识图谱"视觉

---

## 🎨 主题系统

通过 CSS 自定义属性实现,定义在 `:root`(暗色)和 `body.theme-light`(亮色)上:

```css
:root {
  --bg: linear-gradient(180deg, #1a1a1e 0%, #39383d 100%);
  --text: #d3dae3;
  --btn-blue: #4aa3ff;
  /* ... */
}
body.theme-light {
  --bg: #f4f6f8;
  --text: #2a3340;
  /* ... */
}
```

切换时只改 `body` 的 class,所有色变量自动联动。

---

## 🛠️ 技术栈

| 层 | 技术 |
| --- | --- |
| 结构 | 纯 HTML5 |
| 样式 | 原生 CSS3(CSS 变量、Grid、Flexbox、动画) |
| 行为 | 原生 JavaScript(主题切换、入场动画) |
| 字体 | Tenor Sans(Google Fonts 中国镜像) |

**没有引入任何框架或第三方库** —— 一个 HTML 文件就是一个完整的页面。

---

## 📌 路线图

- [ ] 接入真实后端 API,替换硬编码的示例数据
- [ ] 支持自然语言问答输入框(右下角悬浮)
- [ ] 来源对比 / 冲突高亮(不同来源观点不一致时)
- [ ] 实体关系图谱视图(基于 SVG 连线扩展)
- [ ] 移动端交互优化(长按查看来源)

---

## 📄 许可

本项目为原型 / 演示用途,代码可自由参考。

---

## 🙏 致谢

- UI 设计参考自 [Magi](https://magi.com/) ——  Peak Labs 出品的知识搜索引擎
- 字体来自 [Google Fonts](https://fonts.google.com/specimen/Tenor+Sans)
