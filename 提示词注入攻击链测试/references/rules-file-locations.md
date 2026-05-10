# 各产品的规则、指令文件位置

记录会自动影响Agent行为的规则文件。

|产品|文件|格式|自动加载|是否需审批|作用域|持久性|
|---|---|---|---|---|---|---|
|Cursor| `.cursorrules` |文本|是|否|工作区|重启后仍在|
|Cursor| `.cursor/rules/*.mdc` |MDC|是|否|工作区|重启后仍在|
|Windsurf| `.windsurfrules` |文本|是|否|工作区|重启后仍在|
|Cline| `.clinerules` |文本|是|否|工作区|重启后仍在|
|Cline| `.cline/rules/` |目录|是|否|工作区|重启后仍在|
|Claude Code| `CLAUDE.md` |Markdown|是|首次常用为信任提示|工作区及可能父目录|重启后仍在|

# 侦察说明

- 看是否支持多文件合并
- 看是否支持条件加载
- 看父目录是否也会被读取
