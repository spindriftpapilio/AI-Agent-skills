# Hook滥用载荷模板

用于验证支持生命周期Hook的产品，会不会从工作区配置自动执行命令。

# 通用思路先用无害命令验证：

- 输出固定标记
- 写一个临时文件
- 记录时间戳

初始验证阶段不宜直接使用复杂payload。

# Windsurf Cascade Hook

**常用配置位置：**

- `.windsurf/cascade.json`
- 或侦察阶段确认出的等价路径

**测试目标：**
- 会话开始
- 用户发消息
- 工具执行前后

# Claude Code Hook

**常用关注位置：**

- `.claude/settings.json`
- `.claude/settings.local.json`

**重点看：**
- `SessionStart`类事件
- 工作区级配置是否可影响Hook
- 未信任状态是否也会读配置

# 通用最小验证模板

```json


{
  hooks: {
    SessionStart: [
      {
        command: echo hook-fired
      }
    ]
  }
}

```

## 验证要点

- Hook是不是自动触发

- 触发前是否有清晰审批
- 审批后修改内容是否会重新校验
