# 安装指南

## 🚀 快速开始

### 前置条件

1. **OpenClaw 已安装**
   - 如未安装，访问 https://openclaw.ai 下载

2. **Chrome 浏览器 + OpenClaw 扩展**
   - Chrome 浏览器
   - OpenClaw Browser Relay 扩展（用于浏览器自动化）

### 安装步骤

#### 1. 克隆仓库

```bash
git clone https://github.com/YOUR_USERNAME/openclaw-news.git
cd openclaw-news
```

#### 2. 复制配置文件

```bash
# 复制配置模板
cp config/news-daily.json.example ~/.openclaw/workspace/config/news-daily.json
```

#### 3. 修改配置

编辑 `~/.openclaw/workspace/config/news-daily.json`：

```json
{
  "timezone": "Asia/Shanghai",  // 修改为你的时区
  "schedule": "0 8 * * *"       // 修改为需要的发送时间
}
```

#### 4. 启用任务

```bash
openclaw cron enable news-daily
```

#### 5. 测试运行

```bash
openclaw news-daily run --test
```

---

## 📋 详细配置

### 新闻源配置

编辑 `config/news-daily.json` 中的 `sources` 数组：

```json
{
  "sources": [
    {
      "name": "IT 之家",
      "url": "https://www.ithome.com/rss/",
      "category": "tech",
      "limit": 10,
      "priority": 5
    }
  ]
}
```

**参数说明**：
- `name`: 新闻源名称
- `url`: RSS 地址
- `category`: 分类（tech/ai/finance/macro/geek）
- `limit`: 每次抓取条数
- `priority`: 优先级（1-5，越高越重要）

### 推荐新闻源

| 名称 | URL | 类别 |
|------|-----|------|
| IT 之家 | https://www.ithome.com/rss/ | 科技 |
| 36 氪 | https://36kr.com/feed | 科技/创投 |
| InfoQ | https://www.infoq.cn/feed | 技术 |
| 虎嗅 | https://www.huxiu.com/rss/0.xml | 商业 |
| Solidot | https://www.solidot.org/index.rss | 极客 |
| 阮一峰 | https://www.ruanyifeng.com/blog/atom.xml | 技术博客 |

---

## ⚙️ 高级配置

### 自定义分类

```json
{
  "categories": {
    "general": "🔥 头条大事",
    "ai": "🧠 人工智能",
    "tech": "💻 科技/数码"
  },
  "categoryLimits": {
    "general": 5,
    "ai": 8,
    "tech": 6
  }
}
```

### 质量打分配置

```json
{
  "features": {
    "scoring": true,
    "showScore": false,
    "showLowScoreThreshold": 0.6
  },
  "scoring": {
    "weights": {
      "sourceTrust": 0.3,
      "keywordMatch": 0.3,
      "recency": 0.2,
      "categoryPriority": 0.2
    }
  }
}
```

---

## ✅ 验证安装

### 检查配置

```bash
openclaw news-daily check
```

### 测试运行

```bash
# 测试运行一次
openclaw news-daily run --test

# 查看输出
openclaw news-daily run --test --output=test-output.md
```

### 检查定时任务

```bash
# 查看 Cron 状态
openclaw cron status

# 确认任务已启用
openclaw cron list
```

---

## ❓ 故障排查

### 问题 1：配置加载失败

**症状**：
```
Error: Cannot load config/news-daily.json
```

**解决**：
1. 确认文件路径正确
2. 检查 JSON 格式是否有效
3. 确认文件权限

### 问题 2：RSS 抓取失败

**症状**：
```
Error: Failed to fetch RSS feed
```

**解决**：
1. 检查网络连接
2. 验证 RSS 地址是否可访问
3. 检查防火墙设置

### 问题 3：浏览器扩展未连接

**症状**：
```
Error: Browser extension not connected
```

**解决**：
1. 打开 Chrome 浏览器
2. 点击 OpenClaw 扩展图标
3. 确保扩展已激活

---

## 📞 获取帮助

- 查看 [README.md](../README.md)
- 查看 [常见问题](faq.md)
- 提交 Issue：https://github.com/YOUR_USERNAME/openclaw-news/issues

---

_最后更新：2026-02-27_
