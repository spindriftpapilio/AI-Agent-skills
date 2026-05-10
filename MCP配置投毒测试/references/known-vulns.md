# 已知MCP配置投毒漏洞

|产品|漏洞|CVE / Advisory|链接|攻击模型|状态|
|---|---|---|---|---|---|
|Roo Code|工作区不可信MCP配置导致RCE|GHSA-5x8h-m52g-5v54|[GitHub Advisory](https://github.com/RooCodeInc/Roo-Code/security/advisories/GHSA-5x8h-m52g-5v54)|零交互|已修复|
|Cursor|MCPoison：首次审批后修改内容不重验|-|[Checkpoint Research](https://research.checkpoint.com/2025/cursor-vulnerability-mcpoison/)|双阶段|已修复|
|Windsurf|MCP工具调用缺少足够安全控制|-|[embracethered](https://embracethered.com/blog/posts/2025/windsurf-dangers-lack-of-security-controls-for-mcp-server-tool-invocation/)|零交互工具调用|-|
|Amp Code|提示词注入改配置，加入MCP服务|-|[embracethered](https://embracethered.com/blog/posts/2025/amp-agents-that-modify-system-configuration-and-escape/)|PI ->配置|已修复|
|Amazon Kiro|提示词注入加入MCP服务|-|[embracethered](https://embracethered.com/blog/posts/2025/aws-kiro-aribtrary-command-execution-with-indirect-prompt-injection/)|PI ->配置|-|
|通用|MCP协议本身的客户端混淆风险|-|[embracethered](https://embracethered.com/blog/posts/2025/model-context-protocol-security-risks-and-exploits/)|多种|-|

# 观察重点

- 首次审批之后是否重新校验
- settings名称与实际命令是否可分离
- 工作区配置是否能直接影响工具列表
