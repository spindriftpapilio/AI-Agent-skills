# 子Agent与自定义Agent加载位置

## Claude Code

- 用户级：`~/.claude/agents/`
- 项目级：`.claude/agents/`项目级子Agent意味着仓库内容本身就可能参与Agent行为。

来源：

- https://code.claude.com/docs/en/settings

## 测试时要问的问题

- 项目级定义是否默认可见
- UI是否明确告诉用户当前用了哪个子Agent
- 子Agent是否能声明工具权限或工作范围
- 主Agent是否会自动把任务分派给它

