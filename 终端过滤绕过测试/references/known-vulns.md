# 已知终端过滤绕过漏洞

|产品|漏洞|CVE / Advisory|链接|绕过方式|状态|
|---|---|---|---|---|---|
|Claude Code|借allowlist中的DNS工具做数据外传|CVE-2025-55284|[embracethered](https://embracethered.com/blog/posts/2025/claude-code-exfiltration-via-dns-requests/)|`nslookup` / `dig` +shell展开|已修复|
|Amazon Q Developer|`find -exec`参数绕过导致RCE|-|[embracethered](https://embracethered.com/blog/posts/2025/amazon-q-developer-remote-code-execution/)|允许命令中的危险参数|已修复|
|Gemini CLI|解析缺陷导致任意命令执行|-|[xplo1t-sec](https://xplo1t-sec.github.io/posts/exploiting-a-parsing-flaw-in-gemini-cli-to-execute-any-command/)|换行、命令拆分|已修复|
|Mistral Vibe CLI|Shell展开导致执行|-|[Mindgard](https://mindgard.ai/disclosures/mistral-vibe-cli-shell-expansion-command-execution)|`$(...)`等shell展开|-|
|Windsurf|PowerShell过滤绕过|-|[embracethered](https://embracethered.com/blog/posts/2025/windsurf-data-exfiltration-vulnerabilities/)|PowerShell特定技巧|-|

# 规律总结

- 只看命令名，不看参数
- 只看首行，不看完整结构
- 不理解Shell展开
- 不同平台实现不一致
