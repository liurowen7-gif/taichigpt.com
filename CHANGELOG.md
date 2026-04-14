# Changelog · taichigpt.com

---

## v1.0.4 — 2026-04-14

### 订阅文案重构（海外用户）

从"候补名单"话语体系切换至"故事订阅"话语体系，与 Reddit 内容引流策略对齐：

- **导航栏按钮**：Get Early Access → Subscribe Free
- **CTA 区按钮（海外）**：Join Waitlist → Subscribe Free
- **CTA 区说明文字**：Online classes are coming… → Get Tai Chi stories in your inbox — history, philosophy & living tradition. Free, no spam.
- **CTA 订阅成功提示**：You're on the list. See you on the mat. → Subscribed. Stories coming your way.
- **吸底悬浮条按钮**：Get Early Access → Subscribe Free
- **吸底悬浮条成功提示**：You're on the list. → Subscribed. Stories coming your way.

> 背景：通过 Reddit r/taichi 发布太极历史故事帖，帖末引导读者至 taichigpt.com 免费订阅。原文案"Waitlist"与"订阅故事"定位不符，造成预期落差，故统一文案语言。

---

## v1.0.3 — 2026-04-14

### SEO 深度优化

- **hreflang 标签**：声明 EN / ZH 双语版本，帮助 Google 按语言匹配用户
- **`<html lang>` 动态更新**：切换语言时同步更新 lang 属性（en → zh-CN）
- **图片 alt 标签优化**：所有图片改为关键词丰富的描述性 alt 文案
- **图片 lazy loading**：折叠线以下图片加 `loading="lazy"`，提升页面加载速度
- **FAQ Schema**：新增 6 条常见问题结构化数据，覆盖核心搜索意图（什么是混元太极、新加坡课程、冯彦博是谁等），可触发 Google 富摘要
- **爬虫可读内容**：将 14 篇文化故事正文以语义化 HTML 内嵌（视觉隐藏），让 Google 可索引弹窗内容

---

## v1.0.2 — 2026-04-13

### 吸底订阅悬浮条

- 用户滚过 Hero 区（500px）后，底部自动滑出订阅悬浮条
- 文案定位：内容订阅方向（太极文化周报、阴阳哲学、传统智慧），非课程报名
- 含邮箱输入框 + 提交按钮，提交成功后 2.5 秒自动收起
- 靠近页面底部 CTA 区时自动隐藏，避免重叠
- 右侧关闭按钮（×），关闭后本次会话不再弹出（sessionStorage）
- 内容整体水平居中，叉绝对定位贴右
- 双语覆盖（EN / 中文），随语言切换同步更新

---

## v1.0.1 — 2026-04-13

### 文化故事模块

**双层文化区块**
- 新增「太极文化」板块（8张卡片）：鹤蛇之争、陈家沟、杨露禅、阴阳、十三势、融合之道、缠丝劲、易经宇宙观
- 新增「心意混元」板块（6张卡片）：拳种介绍、炼成记、真太极、新加坡缘分、走向世界、修炼之道
- 每张卡片点击后弹出全文阅读弹窗，支持 ESC 关闭、点击遮罩关闭
- 全部文案双语覆盖（EN / 中文）

**图片**
- 太极文化 8 张图片：来自 Wikimedia Commons（公共领域 / CC 协议）
  - 武当宫观、明代建筑、杨露禅画像、阴阳图、八卦图、太极群练、汉代马王堆丝画、莱布尼茨易经六十四卦图
- 心意混元 6 张图片：从冯彦博老师提供的文档中提取
  - 冯志强书封练拳照、年轻冯志强肖像、室外练拳、1985年日本授课、2002年美国授拳、小观园练拳
- 弹窗正文内完整展示原图（不裁剪，保持原始比例）
- 卡片缩略图针对竖幅人像照片修正裁切位置（`center top`）

**导航**
- 顶部导航栏左侧新增「太极文化」「心意混元」两个入口，分别锚点跳转
- 修复「心意混元」导航点击无法滚动的问题（补充 `id="hun-yuan"`）

---

## v1.0.0 — 2026-04-05

### 核心功能

**网站基础**
- 单页静态网站，部署于 GitHub Pages，自定义域名 taichigpt.com
- Namecheap DNS（4条A记录 + CNAME）指向 GitHub Pages

**内容结构**
- Hero 区：标题、副标题、邮件订阅表单
- Stats Bar：700年传承、第12代、3个层次、武术七段
- Philosophy 区：太极拳介绍（3段文字 + 图片）
- Instructor 区：冯彦博老师简介 + 4项资质
- Gallery：3张图片横排展示
- Video 区：嵌入 YouTube 视频（陈式心意混元太极拳24式完整示范）
- Courses 区：3级课程体系（入门/提高/精修）+ 线上/线下双轨道
- Quote 区：太极拳理引言
- CTA 区：底部邮件订阅表单
- Footer：版权信息

**邮件订阅**
- 表单提交 → Cloudflare Worker → Lark/飞书 Bitable 自动存档
- Worker 名称：`taichi-email-collector`（liurowen7.workers.dev）
- Bitable：sgj7v7lu63c.sg.larksuite.com，App Token S28WbbRWlah0DKsNry6lHA0pgnh

**Geo 地理定位**
- 通过 ipapi.co 检测访客 IP
- 新加坡 IP：显示线下课程信息（地址、价格 SGD $580、"Enquire Now"按钮）
- 海外 IP：显示线上课程候补（"Join Waitlist"按钮，Coming Soon）
- 线下/线上 Track 卡片随地理位置高亮/淡化

**双语支持（EN / 中文）**
- 右上角 `EN | 中文` 切换按钮
- 全站文案双语覆盖：所有 section 标题、课程描述、instructor 资质、引言、footer 等
- Geo 动态文案也支持双语（eyebrow、subtitle、按钮、Tracks、表单提示、成功消息）
- 语言选择持久化（localStorage），刷新保留

**其他**
- Google Analytics：G-XEHV8DR3HM
- 粒子动画背景（Canvas）
- 响应式移动端适配
- 拳种名称统一为：**陈式心意混元太极拳**

---

## 待迭代方向（备忘）

- [ ] Lark 自动化：新订阅时飞书通知提醒
- [ ] 更多视频内容上线后嵌入
- [ ] 新加坡课程开班时间、报名链接
- [ ] 线上课程正式开放时更新 CTA
- [ ] SEO 优化（结构化数据、sitemap）
- [ ] 学员评价 / Testimonials 区块
