# 已公开的攻击链案例

这里整理的是已经披露的多阶段真实案例，用来帮助你判断：

- 某条链是否现实可行
- 哪些原语最容易组合
- 厂商通常会如何分级和修复

# 链1：GitHub Copilot提示词注入 -> settings.json -> RCE

**链类型：**经典链

**触发模型：**单次正常交互
**来源：** [embracethered](https://embracethered.com/blog/posts/2025/github-copilot-remote-code-execution-via-prompt-injection/)

**链路概述：**
`克隆仓库 ->恶意内容进入上下文 ->Copilot改写工作区设置 ->IDE调用恶意路径 ->执行`

**关键点：**
- 攻击者把注入放进代码或README
- 用户只是让Copilot正常分析代码
- Agent代写`.vscode/settings.json`
- 设置中的工具路径被指向恶意程序

# 链2：Claude Code项目文件 -> Hook、设置 -> 执行

**来源：** [Checkpoint Research](https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/)

**审查要点：**
- 项目级配置被当成可信输入
- 生命周期Hook可以变成执行入口
- 配置与工作区内容之间的边界不清晰

# 链3：Cursor MCP审批后替换（MCPoison）

**来源：** [Checkpoint Research](https://research.checkpoint.com/2025/cursor-vulnerability-mcpoison/)

**链路概述：**
`用户先批准无害MCP ->配置内容被替换 ->系统沿用旧审批 ->恶意工具生效`

**关键点：**
- 不是第一次审批有问题
- 而是审批后的内容变更没有被重新校验

# 链4：工作区MCP配置自动加载 ->命令执行

**相关来源：**

- [Roo Code Advisory](https://github.com/RooCodeInc/Roo-Code/security/advisories/GHSA-5x8h-m52g-5v54)
- [Mindgard披露集合](https://mindgard.ai/learn/disclosures)

**审查要点：**
- 打开工作区即可触发
- 风险点在自动发现+自动加载+自动执行

# 链5：提示词注入 ->命令生成 ->终端绕过 ->外传、执行

**常用来源：**

- [Claude Code DNS外传](https://embracethered.com/blog/posts/2025/claude-code-exfiltration-via-dns-requests/)
- [Amazon Q`find -exec`](https://embracethered.com/blog/posts/2025/amazon-q-developer-remote-code-execution/)

**审查要点：**
- Agent先被诱导偏离原始任务
- 然后把敏感操作包装成允许命令
- 最终通过Shell特性或危险参数突破过滤

# 使用说明

把这些案例当成参照时，不要只看表面相似性，重点考察以下方面：

- 你的目标是否有相同的自动加载点
- 审批模型是否相似
- 工作区写入能力是否足够连接下一跳
- 是否同样存在工具路径、Hook、设置文件、MCP这些枢纽

