# 公开模式与测试启发

## 厂商文档给出的高影响扩展点

- Anthropic Hook文档明确说明Hook会执行任意Shell命令，并给出多种事件点
- GitHub Copilot Hook文档明确把PreToolUse描述为影响范围最大的扩展点，可用于阻断危险命令和执行策略控制

这说明：

- 任何项目级或团队级可下发的Hook定义，都应被视为高优先级审查面
- 任何子Agent或Hook的权限继承不清晰，都值得单独建立skill进行测试

来源：

- https://code.claude.com/docs/en/hooks
- https://docs.github.com/en/copilot/concepts/agents/cloud-agent/about-hooks

