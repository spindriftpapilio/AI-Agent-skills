# 真实世界的PI ->RCE攻击链示例

用于参考提示词注入如何从模型被诱导偏离原始任务，升级到真实安全影响。

# 示例1：GitHub Copilot PI ->settings.json ->RCE

**来源：** [embracethered](https://embracethered.com/blog/posts/2025/github-copilot-remote-code-execution-via-prompt-injection/)

**模型：**用户正常让Copilot审代码

**链路：**
1. 攻击者把注入内容放在代码或README中
2. 用户正常发起代码分析请求
3. Copilot在响应过程中偏离任务
4. Agent改写`.vscode/settings.json`
5. IDE后续调用恶意可执行路径

# 示例2：提示词注入 ->写MCP / 规则文件 / Hook ->持久化

**共性：**

- 第一次触发常常只是一次正常聊天
- 实质性风险主要来自Agent代写了后续会自动生效的配置

# 分析时应重点审查的事项

- 注入载体是什么
- 用户做了什么正常动作
- Agent到底执行了什么额外动作
- 额外动作是否跨会话持续存在

