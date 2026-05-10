# 公开工具与基准

## Snyk Agent Scan

公开仓库说明它可以发现并扫描Agent组件、MCP配置和skills，还提供`--skills`模式。
仓库还明确给出一个危险选项：`--dangerously-run-mcp-servers`，会跳过交互式同意并启动配置中的stdio MCP服务。

这对测试的启发很明确：

- 扫描器本身也要区分安全模式与危险模式
- 任何会自动启动MCP的治理工具，都需要单独审计其审批边界

来源：

- https://github.com/snyk/agent-scan

## AgentDojo

公开仓库把它定义为用于评估LLM agents提示词注入攻击与防御的动态环境，适合拿来做方法论校验和基准复现实验。

来源：

- https://github.com/ethz-spylab/agentdojo

