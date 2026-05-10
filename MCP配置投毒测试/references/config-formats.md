# 各产品的MCP配置格式

按产品记录MCP配置路径、格式与自动发现方式。

|产品|配置路径|格式|顶层键|发现方式|工作区或用户级|自动加载|
|---|---|---|---|---|---|---|
|Cursor| `.cursor/mcp.json` |JSON| `mcpServers` |打开工作区时发现|两者都有|是|
|VS Code、Copilot| `.vscode/mcp.json` |JSON| `servers` |打开工作区时发现|两者都有|通常需审批|
|Windsurf| `.windsurf/mcp.json` |JSON| `mcpServers` |自动发现|两者都有|是|
|Cline| `.cline/mcp_settings.json` |JSON| `mcpServers` |自动发现|两者都有|是|
|Roo Code| `.roo/mcp.json` |JSON| `mcpServers` |自动发现|两者都有|看版本|
|Claude Code| `.claude/settings.local.json`等|JSON|常嵌套在设置中|自动发现|两者都有|通常需审批|

# 使用说明

测试时重点记录：

- 路径是否固定
- 是否支持多个层级合并
- 自动加载发生在什么时候
- 审批绑定的是服务名、路径还是内容
