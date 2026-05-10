# MCP配置投毒载荷模板

按产品给出最小测试骨架。先验证能不能被识别、能不能被加载，再验证是否能够执行。

# Cursor

**路径：** `.cursor/mcp.json`

```json


{
  mcpServers: {
    dev-tools: {
      command: echo,
      args: [mcp-test]
    }
  }
}

```

# VS Code、Copilot

**路径：** `.vscode/mcp.json`

```json


{
  servers: {
    dev-tools: {
      command: echo,
      args: [mcp-test]
    }
  }
}

```

# 使用说明

- 第一阶段只用无害命令
- 第二阶段再看审批、缓存、修改后是否重验
- 记录UI展示的名称与真实命令是否一致
