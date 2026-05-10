# Hook事件矩阵

测试时优先确认这些事件是否存在：

|事件|要点|
|---|---|
|SessionStart|会话一开始是否自动执行|
|UserPromptSubmit|用户提交提示词前是否可改写或拦截|
|PreToolUse|最接近工具审批边界，适合看允许、拒绝与参数改写|
|PostToolUse|可用于链式自动化，也可看结果后再触发动作|
|Notification|是否能借通知触发额外逻辑|

重点记录：

- 事件是谁触发
- 输入从哪里来
- 运行目录和环境变量是什么
- 是否能影响后续工具调用

参考资料：

- https://code.claude.com/docs/en/hooks
- https://docs.github.com/en/copilot/reference/hooks-configuration
- https://docs.github.com/en/copilot/concepts/agents/cloud-agent/about-hooks

