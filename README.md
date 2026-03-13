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

## 在 Cursor 中使用 Opus 4.6

Cursor IDE 提供了多个 Opus 4.6 变体供选择：

- **Non-Thinking, High Effort**：适用于日常编码、文档处理和通用任务
- **Non-Thinking, Max Effort**：适用于深度搜索和全面信息检索
- **Thinking, High Effort**：适用于复杂编码、调试和代码审查
- **Thinking, Max Effort**：适用于前沿推理和最困难的问题
- **Fast Mode**：更快的变体，适用于对速度敏感的场景

## 通过 API 使用 Opus 4.6

通过 Claude API 调用时，使用模型标识符 `claude-opus-4-6`：

```python
import anthropic

client = anthropic.Anthropic()

message = client.messages.create(
    model="claude-opus-4-6",
    max_tokens=1024,
    messages=[
        {"role": "user", "content": "Hello, Claude!"}
    ]
)
```

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
