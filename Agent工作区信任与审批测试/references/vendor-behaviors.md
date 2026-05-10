# 厂商文档里值得重点核对的行为

## Anthropic Claude Code

- 项目级设置可放在`.claude/settings.json`
- Hook也来自项目文件
- 项目级子Agent可放在`.claude/agents/`这说明工作区配置、Hook、子Agent本身都应被视为信任边界的一部分。

来源：

- https://code.claude.com/docs/en/settings
- https://code.claude.com/docs/en/hooks

## Cursor

- 文档明确提到工作区信任
- 也明确提到第三方MCP需要用户批准
- 这很适合拿来比对实际提示、实际缓存粒度与实际初始化顺序

来源：

- https://docs.cursor.com/account/agent-security
- https://docs.cursor.com/advanced/model-context-protocol

