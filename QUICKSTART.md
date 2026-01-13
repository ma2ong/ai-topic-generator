# 快速启动指南

## 🎯 5 分钟快速上手

### 1️⃣ 安装系统

#### 选项 A：作为 Claude Code Plugin 安装（推荐）

```bash
# 进入项目目录
cd ai-topic-generator

# 安装为 Claude Code plugin
# 方法1: 如果支持本地安装
claude plugin install .

# 方法2: 手动复制到 plugins 目录
cp -r . ~/.claude/plugins/ai-topic-generator
```

#### 选项 B：手动安装 Skills

```bash
# 复制 Skills 到 Claude Code
cp -r skills/hotspot-collector ~/.claude/skills/
cp -r skills/topic-generator ~/.claude/skills/
cp -r skills/topic-reviewer ~/.claude/skills/
```

### 2️⃣ 验证安装

启动 Claude Code：

```bash
claude
```

在对话中输入：

```
列出所有可用的 skills
```

应该能看到：
- ✅ hotspot-collector（热点采集员）
- ✅ topic-generator（选题生成师）
- ✅ topic-reviewer（选题审核官）

### 3️⃣ 开始使用

#### 完整流程（一键生成）

```
开始今日选题生成
```

系统会自动：
1. 采集全网热点 → `output/daily_hotspots/YYYY-MM-DD.json`
2. 生成 TOP10 选题 → `output/generated_topics/YYYY-MM-DD.json`
3. 审核选题质量 → `output/review_reports/YYYY-MM-DD.json`
4. 自动迭代优化直到全部通过

#### 分步执行

**仅采集热点：**
```
使用热点采集员采集今日全网热点
```

**基于已有热点生成选题：**
```
使用选题生成师基于今日热点生成 TOP10 选题
```

**审核生成的选题：**
```
使用选题审核官审核今日生成的选题
```

### 4️⃣ 查看结果

```bash
# 查看热点数据
cat output/daily_hotspots/2026-01-13.json

# 查看生成的选题
cat output/generated_topics/2026-01-13.json

# 查看审核报告
cat output/review_reports/2026-01-13.json
```

## 📊 输出示例

### 最终输出格式

每个选题包含：
- ✅ **事件描述**：what, when, who, background
- ✅ **核心角度**：独特视角、洞察点
- ✅ **标题建议**：主标题 + 备选标题
- ✅ **内容大纲**：章节结构、关键点
- ✅ **元数据**：难度、优先级、预估时间

### 审核报告格式

- ✅ 每个选题的详细评分（5个维度）
- ✅ PASS/REVISE/REJECT 判定
- ✅ 具体、可执行的修改建议
- ✅ 优点和改进方向

## ⚙️ 自定义配置

### 调整选题数量

编辑 `.claude-plugin/plugin.json`：

```json
{
  "config": {
    "default_topic_count": 10  // 改为 5 或 15
  }
}
```

### 调整审核标准

编辑 `skills/topic-reviewer/SKILL.md`，修改权重：

```markdown
### 审核维度
- 选题价值 (权重: 30%)     // 可以调整
- 角度独特性 (权重: 25%)
- 标题质量 (权重: 20%)
- 可执行性 (权重: 15%)
- 受众匹配度 (权重: 10%)
```

### 修改采集平台

编辑 `skills/hotspot-collector/SKILL.md`：

```markdown
### 平台优先级
1. 高优先级：Twitter、Reddit、Github  // 添加或删除平台
2. 中优先级：知乎、微博
3. 低优先级：小红书、B站
```

## 🔧 常见问题

### Q1: 热点采集失败？

**解决方案**：
- 检查网络连接
- 某些平台可能需要 API 密钥
- 可以使用示例数据测试后续流程

### Q2: 所有选题审核不通过？

**解决方案**：
- 降低审核标准（修改通过分数线）
- 检查热点数据质量
- 查看审核反馈，了解具体问题

### Q3: 迭代超过 3 轮仍未通过？

**解决方案**：
- 增加 `MAX_ITERATIONS` 配置
- 人工介入，手动调整部分选题
- 接受当前通过的选题，放弃未通过的

## 💡 高级用法

### 使用示例数据测试

项目已包含示例数据：

```bash
# 直接使用示例热点生成选题
使用选题生成师基于 output/daily_hotspots/example.json 生成选题
```

### 定期自动化运行

创建定时任务（cron job）：

```bash
# 每天早上 9 点运行
0 9 * * * cd /path/to/ai-topic-generator && claude -p "开始今日选题生成"
```

### 集成到工作流

将输出文件对接到：
- 内容管理系统（CMS）
- Notion 数据库
- Slack 通知
- 邮件报告

## 📚 深入学习

- **README.md** - 完整的项目说明
- **AGENTS.md** - 主 Agent 工作原理和配置
- **INSTALL.md** - 详细安装指南
- **skills/*/SKILL.md** - 各个 Skill 的详细文档

## 🎉 开始创作

现在，您只需要一句话：

```
开始今日选题生成
```

就能获得 TOP10 高质量选题，开启高效的内容创作之旅！

---

**需要帮助？** 查看完整文档或提出问题！
