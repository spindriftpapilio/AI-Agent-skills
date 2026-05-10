# 新增方法的实战性评估

下面这张表评估的是现实落地难度、混入正常工作流的难度，以及拿到高价值权限的可能性。

|方法|典型入口|最少交互|常见前提|实战性|判断|
|---|---|---|---|---|---|
|CI提示词注入（Issue / PR / 提交信息）|Issue、PR、提交信息、审查结果|一次正常跑流水线或让Agent处理工单|CI中存在Agent和高权限令牌|高|入口天然存在，和真实开发流程高度重合，命中后常直接碰到仓库写权限、发布权限或云凭证|
|网页提示词注入|网页总结、网页代操作、浏览器Agent任务|用户点一次总结或发起网页任务|浏览器Agent可读取网页，且常带登录态|高|触发动作自然，攻击载体可藏在评论区、隐藏文本、PDF等位置，跨站影响面大|
|截图 / OCR注入|截图理解、Computer Use、图片解析|一次截图分析或桌面操作|产品支持截图理解或OCR，并继续执行动作|中高|对防护和审计都不友好，隐蔽性强，但比纯文本注入更依赖具体产品能力|
|链接预览外传|Slack、Telegram、邮件、工单消息|Agent回复一次消息|消息通道默认启用链接预览|中高|用户可能不用点链接，风险常被低估；是否成立高度依赖消息平台默认设置|
|提示词注入 + 批准绕过 / 沙箱逃逸|README、网页、日志、MCP响应|一次正常分析或执行任务|校验器只看表层命令，或沙箱边界有缺口|中高|一旦打通影响很大，但通常更依赖具体产品实现缺陷，不如前两类通用|
|MCP工具投毒 / Rug Pull / Shadowing|第三方MCP、市场、远端工具描述|安装一次或批准一次|目标接第三方MCP，且UI不完整展示描述|高|很适合长期潜伏，能把一次批准放大成长期劫持，和真实生态趋势高度一致|
|多工具组合毒流（Toxic Flow）|任意能把不可信输入、敏感数据和出站能力接起来的工具集|通常一次正常任务|目标同时具备读、处理敏感数据和出站能力|高|这是很多真实链的上层模型，单点都看似正常，组合后才出事，实战上很常见|

# 评估说明

给“高”的常见原因：

- 默认部署就存在
- 用户动作属于正常操作
- 目标权限含令牌、登录态、仓库写权限、文件系统或网络出站
- 用户界面很难完整展示真实风险

给“中高”的常见原因：

- 方法可行，但更依赖具体产品实现
- 需要目标开启某类特性，如OCR、链接预览、特定命令包装器
- 复现路径比通用提示词注入更长一些

给“中”的常见原因：

- 条件较多
- 需要稀有配置或特定版本
- 很难稳定命中默认用户场景

# 对测试优先级的建议

如果目标是企业内部真实风险评估，建议优先顺序通常是：

1. CI提示词注入
2. 网页提示词注入
3. MCP工具投毒 / Rug Pull / Shadowing
4. 多工具组合毒流
5. 链接预览外传
6. 截图 / OCR注入
7. 批准绕过 / 沙箱逃逸

这里的排序是按“更容易混进真实工作流”来排，不是按理论影响上限来排。

# 参考来源

- [Aikido: PromptPwnd](https://www.aikido.dev/blog/promptpwnd-github-actions-ai-agents)
- [Brave: Indirect Prompt Injection in Comet](https://brave.com/blog/comet-prompt-injection/)
- [Brave: Unseeable prompt injections in screenshots](https://brave.com/blog/unseeable-prompt-injections/)
- [PromptArmor: Data Exfil from Agents in Messaging Apps](https://www.promptarmor.com/resources/llm-data-exfiltration-via-url-previews-%28with-openclaw-example-and-test%29)
- [PromptArmor: Snowflake Cortex AI Escapes Sandbox and Executes Malware](https://www.promptarmor.com/resources/snowflake-ai-escapes-sandbox-and-executes-malware)
- [Anthropic: Computer Use Tool Docs](https://platform.claude.com/docs/en/agents-and-tools/tool-use/computer-use-tool)
- [Invariant: MCP Security Notification: Tool Poisoning Attacks](https://invariantlabs.ai/blog/mcp-security-notification-tool-poisoning-attacks)
- [Invariant: Toxic Flow Analysis](https://invariantlabs.ai/blog/toxic-flow-analysis)
- [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/)
- [MCPTox](https://arxiv.org/abs/2508.14925)
