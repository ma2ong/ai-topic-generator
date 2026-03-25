# AI 选题生成系统

> 一键完成热点采集、选题生成、质量审核的全自动内容选题系统。

## 📢 重要更新

**本项目已集成到 [claude-skills-collection](https://github.com/ma2ong/claude-skills-collection) 写作技能包中！**

如果你已经在使用 claude-skills-collection，无需单独克隆本仓库。直接使用：

```bash
cd ~/.claude/skills
git clone https://github.com/ma2ong/claude-skills-collection.git
```

**claude-skills-collection** 包含：
- ✅ 本项目的完整功能（ai-topic-generator）
- ✅ 全流程写作系统（vibe-writer-pro）
- ✅ AI味审校（ai-proofreading）
- ✅ 内容转换分发（content-converter）
- ✅ 个人素材库搜索（personal-knowledge-search）

**推荐使用集成版**，获得完整的写作工作流支持。

---

## 🎯 一句话开始

```
开始今日选题生成
```

系统会自动：
1. 📡 从多平台采集最新热点（Twitter、Reddit、GitHub、微博、知乎等）
2. 💡 分析并生成 TOP10 高质量选题（含事件描述、核心角度、标题建议）
3. ✅ 智能审核选题质量，给出修改意见
4. 🔄 自动迭代优化，直到所有选题通过审核

**原本需要 2-3 小时的选题工作，现在只需 5-10 分钟！**

---

## 📦 安装

### 方式一：使用集成版（推荐）⭐

```bash
# 获取包含本项目的完整写作技能包
cd ~/.claude/skills
git clone https://github.com/ma2ong/claude-skills-collection.git
```

**优势**：
- 包含完整的写作工作流（选题 → 写作 → 审校 → 分发）
- 自动更新和维护
- 与其他写作工具无缝协作

### 方式二：独立使用

```bash
# 仅使用选题系统
git clone https://github.com/ma2ong/ai-topic-generator.git
```

### 方式三：下载 ZIP

从 [Releases](https://github.com/ma2ong/ai-topic-generator/releases) 下载最新版本。

### 使用方式

在 Claude Code 中打开项目目录，直接说：

```
开始今日选题生成
```

---

## 🚀 快速开始

### 完整流程（一键执行）

```
开始今日选题生成，今天是2026年1月29日
```

### 分步执行

```
# Step 1: 仅采集热点
采集今日全网热点

# Step 2: 基于热点生成选题
基于今日热点生成TOP10选题

# Step 3: 审核选题
审核今日生成的选题
```

### 自定义选项

```
# 调整数量
生成TOP5选题

# 指定领域
只关注AI和机器人领域的热点

# 指定平台
只从GitHub和ProductHunt采集热点
```

---

## 📊 输出示例

执行完成后，系统会生成三个文件：

### 1. 热点数据
`output/daily_hotspots/2026-01-29.json`

```json
{
  "id": "hs-001",
  "title": "Apple选择Gemini而非ChatGPT为新一代Siri提供动力",
  "platform": "Ars Technica",
  "heat_score": 98,
  "category": "AI/科技巨头",
  "summary": "Apple宣布与Google达成多年合作..."
}
```

### 2. 生成选题
`output/generated_topics/2026-01-29.json`

```json
{
  "topic_id": "topic-001",
  "rank": 1,
  "headline": {
    "primary": "苹果\"抛弃\"ChatGPT选择Gemini：万亿美元押注背后的三个真相"
  },
  "core_angle": {
    "angle_title": "为什么Apple放弃了ChatGPT？Gemini做对了什么",
    "key_insights": [
      "Apple选型的三个核心标准",
      "OpenAI vs Google的B2B战争",
      "这笔交易对Anthropic的影响"
    ]
  }
}
```

### 3. 审核报告
`output/review_reports/2026-01-29.json`

```json
{
  "summary": {
    "total_topics": 10,
    "passed": 8,
    "needs_revision": 2,
    "overall_quality": "优秀"
  }
}
```

---

## 📁 项目结构

```
ai-topic-generator/
├── SKILL.md                # 核心Skill定义（统一版）
├── README.md               # 本文件
├── QUICKSTART.md           # 快速启动指南
├── output/
│   ├── daily_hotspots/     # 热点数据存储
│   ├── generated_topics/   # 生成的选题
│   └── review_reports/     # 审核报告
└── skills/                 # 分拆版Skills（可选，向后兼容）
    ├── hotspot-collector/  # 热点采集器
    ├── topic-generator/    # 选题生成器
    ├── topic-reviewer/     # 选题审核官
    └── obsidian-exporter/  # Obsidian导出器
```

---

## ⚙️ 配置

### 审核标准权重

| 维度 | 权重 | 说明 |
|------|------|------|
| 选题价值 | 30% | 时效性、影响力、教育价值 |
| 角度独特性 | 25% | 差异化、洞察深度 |
| 标题质量 | 20% | 价值传递、吸引力 |
| 可执行性 | 15% | 素材充分、时间合理 |
| 受众匹配度 | 10% | 目标明确、需求吻合 |

### 通过标准

- 总分 ≥ 70分
- 单项 ≥ 60%
- 无致命缺陷

---

## 📈 效率对比

| 工作环节 | 传统方式 | 使用本系统 | 提升 |
|---------|---------|-----------|------|
| 热点采集 | 60-90分钟 | 2-3分钟 | **30x** |
| 选题筛选 | 30-60分钟 | 1-2分钟 | **30x** |
| 角度挖掘 | 20-30分钟 | 自动 | **∞** |
| 标题创作 | 10-20分钟 | 自动 | **∞** |
| 质量审核 | 10-15分钟 | 1分钟 | **10x** |
| **总计** | **2-3.5小时** | **5-10分钟** | **20-40x** |

---

## 🔗 完整写作工作流

### 推荐组合使用

配合 [claude-skills-collection](https://github.com/ma2ong/claude-skills-collection) 实现完整闭环：

```
# Step 1: 选题生成（本项目）
开始今日选题生成

# Step 2: 写作（vibe-writer-pro）
启动 Vibe Writer Pro，基于这个选题写文章

# Step 3: 审校（ai-proofreading）
审校这篇文章，降低AI味

# Step 4: 分发（content-converter）
把这篇文章转成X的thread
```

**从选题到发布，一条龙自动化！**

---

## 🛠️ 故障排查

### 热点采集失败
- 检查网络连接
- 增加请求间隔
- 尝试指定特定平台

### 审核一直不通过
- 热点质量不高，尝试换时间采集
- 适当放宽审核标准
- 手动介入调整

### 迭代次数超限
- 人工介入部分选题
- 调整后重新提交

---

## 🌟 相关项目

- **[claude-skills-collection](https://github.com/ma2ong/claude-skills-collection)** - 完整写作技能包（推荐）
  - 包含本项目的所有功能
  - 额外提供写作、审校、分发等能力
  - 统一管理和更新

---

## 📄 许可证

MIT License

---

## 🙏 致谢

- 基于 Claude Code Skills 架构
- 感谢 Anthropic 提供的 AI 能力
- 已集成到 [claude-skills-collection](https://github.com/ma2ong/claude-skills-collection)

---

## 📝 更新日志

### v2.0.0 (2026-01-29)

- ✅ 集成到 claude-skills-collection
- 📝 更新 README，添加集成说明
- 🔗 推荐使用集成版获得完整工作流

### v1.0.0 (2026-01-15)

- ✨ 初始版本发布
- 🎯 自动化选题系统
- 📡 多平台热点采集
- 🔄 智能审核与迭代

---

**开始使用**：

- **推荐**：安装 [claude-skills-collection](https://github.com/ma2ong/claude-skills-collection) 获得完整功能
- **独立使用**：`git clone` 本仓库后，在 Claude Code 中说"开始今日选题生成"即可

GitHub: https://github.com/ma2ong/ai-topic-generator
