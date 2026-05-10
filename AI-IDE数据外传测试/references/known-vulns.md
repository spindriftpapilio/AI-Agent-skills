# 已知数据外传漏洞整理

这里整理了AI IDE里与图片渲染、提示词注入、远程资源加载等相关的公开外传案例。

# Markdown图片外传

|产品|漏洞|链接|通道|状态|
|---|---|---|---|---|
|Amazon Kiro|通过图片渲染带出数据|[embracethered](https://embracethered.com/blog/posts/2025/aws-kiro-aribtrary-command-execution-with-indirect-prompt-injection/)|Markdown图片|-|
|Cline|通过图片渲染带出数据|[embracethered](https://embracethered.com/blog/posts/2025/cline-vulnerable-to-data-exfiltration/)|Markdown图片|-|
|Windsurf|提示词注入后借图片外传|[embracethered](https://embracethered.com/blog/posts/2025/windsurf-data-exfiltration-vulnerabilities/)|Markdown图片|-|
|OpenHands|访问令牌泄露|[embracethered](https://embracethered.com/blog/posts/2025/openhands-the-lethal-trifecta-strikes-again/)|Markdown、复合链|-|

# 其他常用通道

- DNS请求
- 远程schema、模型地址
- WebView远程资源
- 自定义路径或服务名base URL

# 使用方法

把这些案例当成通道清单来用，不要直接当成漏洞清单：

- 先找你的目标里有没有类似通道
- 再看这些通道能否和PI、命令执行、配置修改串起来
