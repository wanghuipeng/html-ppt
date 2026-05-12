---
name: html-ppt
description: AI技术分享HTML PPT生成器。当用户想要创建技术分享演讲稿、想生成PPT网页、想要科技感的演示文稿、想用HTML做演讲PPT、输入分享主题想要生成演示页面时触发。专门用于生成富有科技感、PPT风格的HTML页面，支持知识点展示、代码演示、转场动画、进度指示器和键盘导航，支持分层目录、图片灯箱、照片墙模式。
---

# AI技术分享HTML PPT生成器

输入一个技术分享主题，自动生成一套完整的科技感HTML PPT演示页面。

## 工作流程

### 1. 分析主题并规划内容结构

接收用户的主题，分析该主题的核心知识点和实战内容，规划幻灯片结构：

**推荐结构（10-14页）：**
1. 封面页 - 主题标题 + 副标题
2. 内容概览页 - 大类分类展示
3. 背景介绍/案例（4-5页）
4. 工具开发/实践（4-5页）
5. 效率与演进（1-2页）
6. 总结页 + Q&A

**内容分类原则：**
- 将相似内容归为大类（如：实战案例、工具开发、效率与演进）
- 每个大类下设置子页面
- 内容概览页展示大类结构

### 2. 生成HTML文件

生成的HTML文件必须包含以下组件：

**科技感视觉元素：**
- 暗色渐变背景（深蓝/深紫/黑色渐变）
- 霓虹发光边框和文字效果
- 粒子/网格背景动效
- 流畅的幻灯片转场动画

**分层目录功能：**
- 左侧顶部目录按钮，带闪烁动画
- 点击展开分层目录（分类 → 子页面）
- 点击分类可展开/折叠子项
- 当前页面对应分类自动展开
- 目录支持点击跳转

**图片查看功能：**
- 点击单张图片查看大图
- 当前页多张图片自动进入照片墙模式
- 照片墙支持网格浏览，点击查看大图
- 大图模式支持键盘切换

**PPT交互功能：**
- 左右箭头键翻页
- 点击导航
- 底部进度指示器（点状）
- 页码显示
- ESC键显示全览/关闭目录
- T键快速打开/关闭目录
- 键盘方向键切换图片

**内容展示：**
- 代码高亮（使用Prism.js）
- 图片灯箱预览
- 照片墙模式
- 流程图/时间线

### 3. 分层目录数据结构

```javascript
const tocData = [
  {
    title: '封面',
    icon: '📌',
    items: [
      { index: 0, title: '封面' }
    ]
  },
  {
    title: '实战案例',
    icon: '💡',
    items: [
      { index: 2, title: 'Workbuddy 专家模式' },
      { index: 3, title: 'Review 方案与交付' },
      { index: 4, title: '遇到的问题' },
      { index: 5, title: 'UniApp 组件升级' }
    ]
  },
  {
    title: '工具开发',
    icon: '🛠️',
    items: [
      { index: 6, title: 'Lite MD 桌面应用' },
      { index: 7, title: 'MCP Server' },
      { index: 8, title: 'MCP Server 集成' },
      { index: 9, title: 'Skills' }
    ]
  },
  {
    title: '效率与演进',
    icon: '🚀',
    items: [
      { index: 10, title: '工作效率提升' },
      { index: 11, title: 'AI Coding 演进' }
    ]
  },
  {
    title: '总结',
    icon: '📊',
    items: [
      { index: 12, title: '总结' },
      { index: 13, title: 'Q & A' }
    ]
  }
];
```

### 4. 代码模板

生成后的HTML必须使用以下CDN资源：

```html
<!-- 代码高亮 -->
<link href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/themes/prism-tomorrow.min.css" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/prism.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-javascript.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-typescript.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-bash.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-json.min.js"></script>
```

### 5. 生成文件结构

```
output/
├── presentation.html    # 主演示文件（单文件，包含内联CSS/JS）
└── assets/             # 资源文件夹（如有额外资源）
```

## 输出要求

### 文件命名
- 演示文件：`{主题名}-presentation.html`
- 例如：`项目实战情况-presentation.html`

### HTML规范
- 使用HTML5语义化标签
- 所有CSS内联到`<style>`标签
- 所有JS内联到`<script>`标签
- 确保无外部依赖（除CDN外）

### 幻灯片模板

**封面页：**
```html
<section class="slide slide-cover" data-slide="1" data-title="封面">
  <div class="grid-bg"></div>
  <div class="slide-content">
    <h1>{主题}</h1>
    <p class="subtitle">{副标题}</p>
    <div class="tech-badge">AI CODING</div>
  </div>
</section>
```

**带图片的内容页：**
```html
<section class="slide" data-slide="3" data-title="示例页面">
  <div class="grid-bg"></div>
  <div class="slide-content">
    <h2>{标题}</h2>
    <div class="two-col">
      <div>
        <!-- 文字内容 -->
      </div>
      <div class="card">
        <h3>{图片标题}</h3>
        <div class="screenshot-container">
          <img src="{图片URL}" alt="描述" class="screenshot" onclick="openLightbox(this)">
        </div>
      </div>
    </div>
  </div>
</section>
```

## 样式规范

### 配色方案（极客风格 - 推荐）

使用GitHub深色风格的配色方案：

```css
:root {
  --bg-primary: #0D1117;
  --bg-secondary: #161B22;
  --bg-card: #161B22;
  --accent-cyan: #00E5FF;
  --accent-blue: #3B82F6;
  --accent-purple: #8B5CF6;
  --accent-pink: #ec4899;
  --accent-orange: #f97316;
  --accent-green: #10B981;
  --accent-red: #F43F5E;
  --text-primary: #FFFFFF;
  --text-secondary: #94A3B8;
  --text-muted: #64748B;
  --neon-glow: 0 0 20px rgba(0, 229, 255, 0.5);
  --accent-primary: #00E5FF;
  --accent-secondary: #3B82F6;
  --gradient-accent: linear-gradient(135deg, var(--accent-cyan), var(--accent-blue));
  --shadow-soft: 0 4px 20px rgba(0, 0, 0, 0.3);
  --shadow-hover: 0 8px 30px rgba(0, 0, 0, 0.4);
  --border-color: #30363D;
}
```

### 目录按钮样式

```css
.toc-toggle {
  position: fixed;
  left: 20px;
  top: 20px;
  width: 40px;
  height: 40px;
  background: rgba(13, 17, 23, 0.95);
  border: 1px solid #30363D;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 200;
  transition: all 0.3s ease;
  animation: toc-blink 2.5s ease-in-out infinite;
}

.toc-toggle:hover {
  background: rgba(0, 229, 255, 0.2);
  border-color: rgba(0, 229, 255, 0.5);
  transform: scale(1.05);
}

@keyframes toc-blink {
  0%, 100% { box-shadow: 0 0 8px rgba(0, 229, 255, 0.2); }
  50% { box-shadow: 0 0 20px rgba(0, 229, 255, 0.4); }
}
```

### 分层目录样式

```css
/* 目录面板 */
.toc-panel {
  position: fixed;
  left: 0;
  top: 0;
  width: 300px;
  height: 100vh;
  background: #0D1117;
  border-right: 1px solid #30363D;
  z-index: 300;
  transform: translateX(-100%);
  transition: transform 0.35s cubic-bezier(0.4, 0, 0.2, 1);
  display: flex;
  flex-direction: column;
}

/* 分类组 */
.toc-group {
  margin-bottom: 8px;
}

.toc-group-header {
  padding: 10px 20px 6px;
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.toc-group-header:hover {
  background: rgba(0, 229, 255, 0.1);
}

.toc-group-icon {
  width: 24px;
  height: 24px;
  background: rgba(0, 229, 255, 0.15);
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.75rem;
  color: var(--accent-cyan);
}

.toc-group.open .toc-group-icon {
  background: var(--accent-cyan);
  color: #0D1117;
}

.toc-group-title {
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--text-primary);
  flex: 1;
}

.toc-group-arrow {
  font-size: 0.7rem;
  color: var(--text-secondary);
  transition: transform 0.2s ease;
}

.toc-group.open .toc-group-arrow {
  transform: rotate(90deg);
}

.toc-group-items {
  display: none;
  padding-left: 12px;
}

.toc-group.open .toc-group-items {
  display: block;
}

/* 子项 */
.toc-item {
  padding: 8px 16px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 10px;
  transition: all 0.2s ease;
  border-left: 2px solid transparent;
  margin-left: 20px;
}

.toc-item:hover {
  background: rgba(0, 229, 255, 0.08);
}

.toc-item.active {
  background: rgba(0, 229, 255, 0.12);
  border-left-color: var(--accent-cyan);
}

.toc-item-num {
  width: 22px;
  height: 22px;
  background: rgba(0, 229, 255, 0.2);
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.7rem;
  font-weight: 600;
  color: #00E5FF;
  flex-shrink: 0;
}

.toc-item.active .toc-item-num {
  background: var(--accent-cyan);
  color: #0D1117;
}

.toc-item-title {
  font-size: 0.85rem;
  color: #E2E8F0;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```

### 内容居中布局

```css
.slide-content {
  max-width: 1200px;
  width: 95%;
  text-align: center;
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100%;
  padding: 40px 0;
}

.slide-cover .slide-content {
  text-align: center;
  justify-content: center;
}

.slide-cover .slide-content > * {
  text-align: center;
}

/* 子元素内容左对齐 */
.slide-content h2,
.slide-content h3,
.slide-content p,
.slide-content ul,
.slide-content .card,
.slide-content .two-col {
  text-align: left;
  width: 100%;
}
```

### 标签样式（保证可读性）

```css
.tag {
  display: inline-block;
  padding: 0.2rem 0.6rem;
  border-radius: 9999px;
  font-size: 0.8rem;
  font-weight: 500;
  margin-right: 0.4rem;
  margin-bottom: 0.4rem;
}

.tag-cyan {
  background: rgba(0, 229, 255, 0.15);
  color: var(--accent-cyan);
  border: 1px solid rgba(0, 229, 255, 0.3);
}

.tag-purple {
  background: rgba(59, 130, 246, 0.15);
  color: var(--accent-blue);
  border: 1px solid rgba(59, 130, 246, 0.3);
}

.tag-green {
  background: rgba(16, 185, 129, 0.15);
  color: var(--accent-green);
  border: 1px solid rgba(16, 185, 129, 0.3);
}

.tag-orange {
  background: rgba(249, 115, 22, 0.15);
  color: var(--accent-orange);
  border: 1px solid rgba(249, 115, 22, 0.3);
}

.tag-pink {
  background: rgba(236, 72, 153, 0.15);
  color: var(--accent-pink);
  border: 1px solid rgba(236, 72, 153, 0.3);
}
```

### 图片样式

```css
.screenshot {
  max-width: 100%;
  max-height: 200px;
  border-radius: 8px;
  border: 1px solid rgba(0, 229, 255, 0.3);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
  cursor: pointer;
  transition: all 0.3s ease;
}

.screenshot:hover {
  transform: scale(1.02);
  box-shadow: 0 6px 30px rgba(0, 229, 255, 0.3);
}

.screenshot-small {
  max-height: 140px;
}

.screenshot-container {
  display: flex;
  flex-wrap: wrap;
  gap: 0.8rem;
  justify-content: center;
  margin-top: 0.8rem;
}
```

### 高亮框样式

```css
.highlight-box {
  background: rgba(0, 229, 255, 0.1);
  border-left: 4px solid var(--accent-cyan);
  padding: 1rem 1.5rem;
  border-radius: 0 8px 8px 0;
  margin: 1rem 0;
}

.highlight-box.orange {
  background: rgba(249, 115, 22, 0.1);
  border-left-color: var(--accent-orange);
}

.highlight-box.green {
  background: rgba(16, 185, 129, 0.1);
  border-left-color: var(--accent-green);
}

.highlight-box p {
  margin: 0;
  color: var(--text-primary);
}
```

### 流程步骤样式

```css
.flow-steps {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  flex-wrap: wrap;
  margin: 1.5rem 0;
}

.flow-step {
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  padding: 0.8rem 1.2rem;
  border-radius: 8px;
  font-size: 0.95rem;
  color: var(--text-secondary);
}

.flow-arrow {
  color: var(--accent-cyan);
  font-size: 1.2rem;
}
```

### 时间线样式

```css
.timeline {
  position: relative;
  padding-left: 2rem;
  margin: 1.5rem 0;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(to bottom, var(--accent-cyan), var(--accent-purple));
}

.timeline-item {
  position: relative;
  padding-bottom: 1.5rem;
}

.timeline-item::before {
  content: '';
  position: absolute;
  left: -2rem;
  top: 0.3rem;
  width: 12px;
  height: 12px;
  background: var(--accent-cyan);
  border-radius: 50%;
  transform: translateX(-5px);
}

.timeline-item:last-child {
  padding-bottom: 0;
}

.timeline-item h3 {
  color: var(--accent-cyan);
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
}

.timeline-item p {
  margin: 0.3rem 0;
}
```

### 概览网格卡片

```css
.overview-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  margin-top: 2rem;
}

.overview-card {
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  padding: 1.5rem;
  text-align: left;
  transition: all 0.3s ease;
}

.overview-card:hover {
  border-color: var(--accent-cyan);
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 229, 255, 0.1);
}

.overview-card h3 {
  margin: 0 0 0.8rem;
  font-size: 1.2rem;
}

.overview-card p {
  font-size: 0.95rem;
  margin: 0;
}
```

### 章节头部样式

```css
.section-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.section-icon {
  width: 48px;
  height: 48px;
  background: rgba(0, 229, 255, 0.15);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
}
```

### 卡片样式

```css
.card {
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  padding: 1.2rem;
  margin: 0.8rem 0;
}

.card h3 {
  margin-top: 0;
  color: var(--accent-cyan);
}
```

### 多列布局

```css
.two-col {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
  align-items: start;
}

.two-col img {
  max-width: 100%;
}

.three-col {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
}
```

### 封面页样式

```css
.slide-cover {
  background: radial-gradient(ellipse at center, #1a1f35 0%, var(--bg-primary) 70%);
}

.slide-cover h1 {
  font-size: 3.5rem;
  font-weight: 700;
  background: linear-gradient(135deg, var(--accent-cyan), var(--accent-blue), var(--accent-purple));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 1rem;
  text-shadow: 0 0 60px rgba(0, 229, 255, 0.3);
}

.slide-cover .subtitle {
  font-size: 1.5rem;
  color: var(--text-secondary);
  margin-bottom: 2rem;
}

.tech-badge {
  display: inline-block;
  padding: 0.5rem 1.5rem;
  background: rgba(0, 229, 255, 0.15);
  border: 1px solid rgba(0, 229, 255, 0.4);
  border-radius: 9999px;
  font-size: 1rem;
  font-weight: 600;
  color: var(--accent-cyan);
  letter-spacing: 0.1em;
}
```

### 目录遮罩层

```css
.toc-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.6);
  z-index: 250;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}

.toc-overlay.open {
  opacity: 1;
  visibility: visible;
}
```

### 灯箱样式

```css
.lightbox {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.95);
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}

.lightbox.active {
  opacity: 1;
  visibility: visible;
}

.lightbox img {
  max-width: 90%;
  max-height: 90%;
  border-radius: 8px;
  box-shadow: 0 0 40px rgba(0, 0, 0, 0.5);
}

.lightbox-close {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 44px;
  height: 44px;
  background: rgba(255, 255, 255, 0.1);
  border: none;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.2s ease;
}

.lightbox-close:hover {
  background: rgba(255, 255, 255, 0.2);
}
```

### 照片墙模式

```css
.photo-wall {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.95);
  z-index: 500;
  padding: 60px 40px 80px;
  display: flex;
  flex-direction: column;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}

.photo-wall.active {
  opacity: 1;
  visibility: visible;
}

.photo-wall-grid {
  flex: 1;
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  overflow-y: auto;
  justify-content: center;
  align-content: flex-start;
}

.photo-wall-item {
  max-width: calc(33.33% - 16px);
  max-height: 250px;
  cursor: pointer;
  border-radius: 10px;
  overflow: hidden;
  border: 2px solid transparent;
  transition: all 0.3s ease;
}

.photo-wall-item:hover {
  border-color: var(--accent-cyan);
  transform: scale(1.03);
}
```

## 幻灯片转场动画规范

**核心原则：标题与内容分离动画，避免闪烁，形成视觉层次**

```css
/* 动画关键帧定义 */
@keyframes titleSlide {
  from { opacity: 0; transform: translateY(-20px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* 切换时内容立即显示，避免闪烁 - 关键！ */
.slide .slide-content > * {
  opacity: 1;
  transform: translateY(0);
}

/* 标题单独动画 - 更明显的入场效果 */
.slide.active .slide-content > h2 {
  animation: titleSlide 0.6s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

/* 封面标题特殊处理 */
.slide.active.slide-cover h1 {
  animation: titleSlide 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

/* 内容区域延迟入场，形成视觉隔离 */
.slide.active .slide-content > *:not(h2):not(h1) {
  opacity: 0;
  animation: fadeInUp 0.5s ease forwards;
  animation-delay: 0.3s;
}

.slide.active .slide-content > *:nth-child(2) { animation-delay: 0.35s; }
.slide.active .slide-content > *:nth-child(3) { animation-delay: 0.45s; }
.slide.active .slide-content > *:nth-child(4) { animation-delay: 0.55s; }
.slide.active .slide-content > *:nth-child(5) { animation-delay: 0.65s; }
.slide.active .slide-content > *:nth-child(n+6) { animation-delay: 0.7s; }

/* 封面页不需要延迟 */
.slide.active.slide-cover .slide-content > * {
  animation-delay: 0s !important;
  opacity: 1 !important;
}
```

**动画设计要点：**
1. **标题先于内容**：标题从上方向下滑入（translateY: -20px → 0）
2. **内容延迟入场**：内容在标题动画完成后约0.3s开始渐入，避免视觉混淆
3. **防闪烁处理**：`.slide .slide-content > *` 默认 opacity: 1，确保切换时内容立即可见
4. **贝塞尔曲线**：使用 `cubic-bezier(0.16, 1, 0.3, 1)` 让动画更自然流畅
5. **封面页特殊处理**：封面所有元素同时动画，不需要延迟

## 快捷键

| 按键 | 功能 |
|------|------|
| → / Space | 下一页 |
| ← | 上一页 |
| ESC | 关闭弹层/全览 |
| F | 全屏模式 |
| T | 打开/关闭目录 |
| ↑ / ↓ | 大图模式切换图片 |
| Home | 第一页 |
| End | 最后一页 |

## 注意事项

- 生成代码时使用实际可运行的示例代码
- 动画效果要流畅，避免卡顿
- 确保代码高亮正确
- 幻灯片数量控制在10-15页为宜
- 目录分类要合理，便于导航
- 生成后立即在浏览器打开验证效果
- 图片使用 `onclick="openLightbox(this)"` 绑定点击事件
- **配色方案**：推荐使用极客风格（GitHub深色风格），避免使用过亮的紫色导致文字看不清
- **文字可读性**：确保所有文字与背景有足够的对比度，标签背景使用半透明配色
- **内容居中**：`.slide-content` 设置 `text-align: center` 和 `align-items: center`，子元素内容左对齐
