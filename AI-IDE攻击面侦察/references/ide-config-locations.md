# IDE工作区配置位置

记录常见AI IDE与Agent会从工作区读取的配置位置。

>这不是完整列表。新版本和扩展会不断增加新路径，所以仍然需要做黑盒观察。

# 已知常用路径

|产品|配置路径|格式|用途|自动加载|备注|
|---|---|---|---|---|---|
|Cursor| `.cursor/mcp.json` |JSON|MCP服务器配置|是|服务器定义会进入Agent上下文|
|Cursor| `.cursor/rules/*.mdc` |Markdown、MDC|项目规则|是|常按文件拆分|
|VS Code、Copilot| `.vscode/settings.json` |JSON|工作区设置|是|高优先级执行面|
|VS Code、Copilot| `.vscode/mcp.json` |JSON|MCP配置|视版本|常伴随审批|
|Windsurf| `.windsurf/mcp.json` |JSON|MCP配置|是|需结合版本验证|
|Windsurf| `.windsurfrules` |文本|项目规则|是|影响Agent行为|
|Cline| `.cline/mcp_settings.json` |JSON|MCP配置|是|也可能存在全局配置|
|Cline| `.clinerules` |文本|规则文件|是|常为零摩擦输入面|
|Claude Code| `CLAUDE.md` |Markdown|指令文件|是|作用域可能向父目录扩展|
|Claude Code| `.claude/settings.json` |JSON|项目设置、Hook、MCP|视版本|高优先级配置面|

# 使用方法

侦察时先按这个表找，再结合：

- 文件读取日志
- 打开项目时的行为
- 文档与更新日志

