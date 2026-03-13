# Claude Opus 4.6 客户端兼容性

## 结论：客户端可以使用 Opus 4.6

Claude Opus 4.6 已于 2026 年 2 月 5 日发布，目前已在多个客户端和平台上全面可用。

## 支持的客户端与平台

| 客户端/平台 | 支持状态 | 模型标识符 |
|---|---|---|
| Cursor IDE | ✅ 原生支持 | 在模型选择器中直接选择 |
| Claude API | ✅ 可用 | `claude-opus-4-6` |
| Amazon Bedrock | ✅ 可用 | 通过 AWS 控制台配置 |
| Google Cloud Vertex AI | ✅ 可用 | 通过 GCP 控制台配置 |
| Microsoft Foundry | ✅ 可用 | 通过 Azure 控制台配置 |
| Claude Code CLI | ✅ 默认模型（v2.1.73+） | 自动使用 |

## 如何在 Cursor 中添加和使用 Opus 4.6

### 前提条件

- 安装最新版本的 Cursor IDE（从 [cursor.sh](https://cursor.sh) 下载）
- 拥有 Cursor 账号并登录（个人计划每月包含 $20 的 API 使用额度）

### 方法一：通过模型下拉菜单选择（推荐）

1. **打开 Cursor 聊天面板**
   - 使用快捷键 `Cmd + L`（macOS）或 `Ctrl + L`（Windows/Linux）打开 Chat
   - 或使用 `Cmd + I` / `Ctrl + I` 打开 Composer

2. **找到模型下拉菜单**
   - 在 AI 输入框的下方，有一个模型选择下拉菜单
   - 默认可能显示为 `Auto` 或其他已选模型

3. **选择 Claude Opus 4.6**
   - 点击下拉菜单，在列表中找到 `Claude Opus 4.6` 相关选项
   - 根据需要选择合适的变体：
     - **Non-Thinking, High Effort** — 日常编码、文档处理、通用任务
     - **Non-Thinking, Max Effort** — 深度搜索和全面信息检索
     - **Thinking, High Effort** — 复杂编码、调试和代码审查
     - **Thinking, Max Effort** — 前沿推理和最困难的问题
     - **Fast Mode** — 对速度敏感的场景

4. **开始使用**
   - 选择模型后，直接在输入框中输入问题或指令即可

### 方法二：通过设置页面添加模型

1. **打开 Cursor 设置**
   - 使用快捷键 `Cmd + ,`（macOS）或 `Ctrl + ,`（Windows/Linux）
   - 或点击左下角齿轮图标进入设置

2. **导航到模型设置**
   - 进入 **Cursor Settings > Models > Model Names**

3. **添加模型**
   - 如果 `Claude Opus 4.6` 没有出现在默认列表中，可以手动添加
   - 在模型名称输入框中输入 `claude-opus-4-6` 并确认

4. **返回聊天面板使用**
   - 添加后，模型将出现在下拉菜单中可供选择

### 方法三：通过 Inline Edit 使用

1. 在编辑器中选中一段代码
2. 按 `Cmd + K`（macOS）或 `Ctrl + K`（Windows/Linux）
3. 在弹出的输入框下方选择 `Claude Opus 4.6`
4. 输入修改指令

### 常用快捷键速查

| 功能 | macOS | Windows/Linux |
|---|---|---|
| 打开 Chat | `Cmd + L` | `Ctrl + L` |
| 打开 Composer | `Cmd + I` | `Ctrl + I` |
| Inline Edit | `Cmd + K` | `Ctrl + K` |
| Terminal AI | 在终端中 `Cmd + K` | 在终端中 `Ctrl + K` |
| 打开设置 | `Cmd + ,` | `Ctrl + ,` |

## 如何通过 Claude Code CLI 使用 Opus 4.6

### 安装或更新 Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

确保版本 ≥ 2.1.73，该版本已将默认模型升级为 Opus 4.6。

```bash
claude --version
```

### 直接使用

Claude Code CLI v2.1.73+ 默认使用 Opus 4.6，直接运行即可：

```bash
claude
```

## 如何通过 API 使用 Opus 4.6

### Python（使用 Anthropic SDK）

```bash
pip install anthropic
```

```python
import anthropic

client = anthropic.Anthropic(api_key="your-api-key")

message = client.messages.create(
    model="claude-opus-4-6",
    max_tokens=1024,
    messages=[
        {"role": "user", "content": "Hello, Claude!"}
    ]
)

print(message.content[0].text)
```

### TypeScript/JavaScript（使用 Anthropic SDK）

```bash
npm install @anthropic-ai/sdk
```

```typescript
import Anthropic from "@anthropic-ai/sdk";

const client = new Anthropic({ apiKey: "your-api-key" });

const message = await client.messages.create({
  model: "claude-opus-4-6",
  max_tokens: 1024,
  messages: [
    { role: "user", content: "Hello, Claude!" }
  ],
});

console.log(message.content[0].text);
```

### 使用 Extended Thinking（推理模式）

```python
import anthropic

client = anthropic.Anthropic(api_key="your-api-key")

message = client.messages.create(
    model="claude-opus-4-6",
    max_tokens=16000,
    thinking={
        "type": "enabled",
        "budget_tokens": 10000
    },
    messages=[
        {"role": "user", "content": "分析这段代码的性能瓶颈..."}
    ]
)
```

### 通过 Amazon Bedrock 使用

```python
import boto3
import json

client = boto3.client("bedrock-runtime", region_name="us-east-1")

response = client.invoke_model(
    modelId="anthropic.claude-opus-4-6-v1",
    body=json.dumps({
        "anthropic_version": "bedrock-2023-05-31",
        "max_tokens": 1024,
        "messages": [
            {"role": "user", "content": "Hello, Claude!"}
        ]
    })
)
```

### 通过 OpenRouter 使用

```python
import openai

client = openai.OpenAI(
    base_url="https://openrouter.ai/api/v1",
    api_key="your-openrouter-key"
)

response = client.chat.completions.create(
    model="anthropic/claude-opus-4-6",
    messages=[
        {"role": "user", "content": "Hello, Claude!"}
    ]
)
```

## 故障排除："No models available" 问题

如果你在 Cursor Settings > Models 中输入 `claude-opus-4-6` 后看到 **"No models available"** 错误，请按以下步骤逐一排查：

### 原因一：需要配置 Anthropic API Key（最常见）

自 2026 年 1 月起，Anthropic 封锁了通过消费者订阅 OAuth token 的自动访问。现在需要手动配置 API Key：

1. 前往 [console.anthropic.com](https://console.anthropic.com/) 注册/登录
2. 在 **API Keys** 页面生成一个新的 API Key
3. 回到 Cursor，进入 **Settings > Models > API Keys**
4. 展开 **API Keys** 部分，在 **Anthropic API Key** 栏填入你的 Key
5. 保存后重新尝试添加模型

### 原因二：模型名称格式问题

Cursor 的模型验证可能不识别短名称 `claude-opus-4-6`。尝试使用**完整的带日期后缀**的模型名称：

```
claude-opus-4-6-20260205
```

在 Settings > Models > Model Names 输入框中输入上述名称后点击 **Add**。

### 原因三：Cursor 版本过旧

确保你的 Cursor 是最新版本：
1. 点击 Cursor 菜单 > **Check for Updates**
2. 或从 [cursor.sh](https://cursor.sh) 重新下载安装最新版

### 原因四：缓存损坏

清除 Cursor 的模型缓存：

**macOS：**
```bash
rm -rf ~/Library/Application\ Support/Cursor/Cache
rm -rf ~/Library/Application\ Support/Cursor/CachedData
```

**Windows：**
```bash
del /q %APPDATA%\Cursor\Cache\*
del /q %APPDATA%\Cursor\CachedData\*
```

**Linux：**
```bash
rm -rf ~/.config/Cursor/Cache
rm -rf ~/.config/Cursor/CachedData
```

清除后完全退出并重启 Cursor。

### 原因五：使用强制刷新

在 Cursor 中按 `Ctrl + Shift + R`（macOS 为 `Cmd + Shift + R`）强制刷新，然后重新进入模型设置。

### 调试技巧

打开 Cursor 的开发者工具查看详细错误信息：
- macOS: `Cmd + Option + I`
- Windows/Linux: `Ctrl + Shift + I`

在 Console 面板中查看是否有关于模型加载或 API 认证的错误日志。

### 推荐的完整操作流程

如果你刚开始使用，建议按此顺序操作：

1. 更新 Cursor 到最新版本
2. 在 **Settings > Models > API Keys** 中填入 Anthropic API Key
3. 在 **Settings > Models > Model Names** 中输入 `claude-opus-4-6-20260205` 并点击 Add
4. 如果仍然失败，清除缓存后重启 Cursor 再试
5. 回到 Chat 面板，在模型下拉菜单中选择新添加的模型

## 模型参数

| 参数 | 值 |
|---|---|
| 上下文窗口 | 200K tokens（标准）/ 1M tokens（Beta，仅 Claude 平台） |
| 输入价格 | $5 / 百万 tokens |
| 输出价格 | $25 / 百万 tokens |
| 缓存写入价格 | $6.25 / 百万 tokens |
| 超过 200K tokens 输入 | 价格翻倍 |

## 主要特性

- 百万级 token 上下文窗口，可理解整个项目
- 卓越的代码审查能力
- 跨多轮对话的意图追踪
- 混合推理（Hybrid Reasoning）能力
- 在 Terminal-Bench 2.0 上达到 65.4% 的得分

## 成本优化建议

- 使用 **Prompt Caching** 可节省高达 90% 的输入成本
- 使用 **Batch Processing** 可节省 50% 的成本
- 对于日常任务选择 **High Effort** 而非 Max Effort 以平衡成本与质量
- 对于速度敏感的场景可选择 **Fast Mode** 变体
