# 公开案例

## Claude Code项目配置与信任前执行

- Check Point Research在2026年披露，Claude Code的项目级`.claude/settings.json`与`.mcp.json`可成为执行面，且其研究展示了Hook、项目MCP与环境变量控制带来的风险。
- 重点不在单一功能，更在项目级配置、信任提示和执行顺序之间的组合。

来源：

- https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/
- https://code.claude.com/docs/en/settings
- https://code.claude.com/docs/en/hooks

## Cursor MCP Special Files与敏感文件保护

- Cursor公开安全公告提到，若敏感MCP文件不存在，Agent可被间接提示词注入链带去创建该文件，从而进一步触发RCE。
- 这类问题很适合归到敏感文件保护与审批边界测试，而不只是提示词注入本身。

来源：

- https://github.com/cursor/cursor/security/advisories/GHSA-4cxx-hrm3-49rm
- https://research.checkpoint.com/2025/cursor-vulnerability-mcpoison/

