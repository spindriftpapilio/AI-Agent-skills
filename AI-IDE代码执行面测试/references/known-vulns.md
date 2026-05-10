# 已知代码执行漏洞（非MCP、非终端过滤）整理

这里整理了与Hook滥用、二进制植入、IDE设置利用、工具自动加载等相关的公开案例。

# Hook滥用

|产品|漏洞|链接|触发模型|状态|
|---|---|---|---|---|
|Windsurf|通过Hooks实现任意代码执行|[embracethered](https://embracethered.com/blog/posts/2025/windsurf-data-exfiltration-vulnerabilities/)|工作区配置|-|
|Claude Code|通过`SessionStart`hooks执行|[Checkpoint Research](https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/)|零交互、项目配置|已修复（文中版本）|

# 二进制植入

|产品类型|典型风险|
|---|---|
|基于VS Code的IDE|打开项目或扩展激活时调用工作区中的同名程序|
|CLI Agent|调用`git`、`python`、`node`等时被PATH劫持|

# 设置滥用

|场景|典型风险|
|---|---|
|工作区设置指定可执行路径|低交互成本升级到执行|
|启动器、校验器、格式化器路径可控|文件打开或扩展激活时触发|

# 使用方式

如果你的目标与这些案例结构相似，优先排查：

- 是否有相同的配置入口
- 是否同样把工作区设置视为可信
- 是否有自动触发的工具链
