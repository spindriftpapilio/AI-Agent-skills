# 真实案例补充

这里整理的是更偏浏览器Agent、CI流程、截图理解和消息通道的真实案例，适合拿来补齐现有skill体系里的空白面。

# 案例1：GitHub Actions / GitLab CI中的Agent提示词注入（PromptPwnd）

**来源：** [Aikido Security](https://www.aikido.dev/blog/promptpwnd-github-actions-ai-agents)

**基本链路：**

1. 攻击者把恶意指令放进Issue、PR描述、提交信息等不可信字符串
2. CI里的Agent把这些内容拼进提示词
3. Agent继续调用高权限工具或执行Shell
4. 令牌、工作流结果或仓库状态被操控

**重点价值：**

- 非常贴近真实企业流程
- 入口天然存在，通常不需要单独造环境
- 常与高权限令牌、制品发布权限、仓库写权限共存

# 案例2：网页总结触发浏览器Agent跨站操作

**来源：** [Brave: Indirect Prompt Injection in Perplexity Comet](https://brave.com/blog/comet-prompt-injection/)

**基本链路：**

1. 攻击者把恶意内容藏进网页、评论区、隐藏文本或其他页面内容
2. 用户点击“总结当前页面”或发起类似网页任务
3. 浏览器Agent把网页内容和用户请求一起送给模型
4. 模型把恶意内容当成可执行指令，继续调用浏览器能力
5. 已登录站点中的敏感数据被读取或被带出

**重点价值：**

- 用户动作非常自然
- 一旦浏览器共享登录态，影响范围会放大
- 传统SOP / CORS思路对Agent行为约束有限

# 案例3：截图 / OCR中的不可见提示词注入

**来源：** [Brave: Unseeable prompt injections in screenshots](https://brave.com/blog/unseeable-prompt-injections/)

**基本链路：**

1. 攻击者把恶意内容放进截图、页面视觉元素或图片文字
2. Agent通过截图理解或OCR读取这些内容
3. 模型把这些视觉内容误当成任务指令
4. 后续点击、输入、导航或数据读取动作被带偏

**重点价值：**

- 适合绕过只盯文本输入的防护
- 对Computer Use和浏览器Agent尤其相关
- 用户往往很难肉眼发现

# 案例4：消息通道中的链接预览外传

**来源：** [PromptArmor: Data Exfil from Agents in Messaging Apps](https://www.promptarmor.com/resources/llm-data-exfiltration-via-url-previews-%28with-openclaw-example-and-test%29)

**基本链路：**

1. 间接提示词注入让Agent生成一个带敏感数据的攻击者URL
2. Agent把这个URL发回Slack、Telegram等消息通道
3. 消息系统自动生成链接预览
4. 预览请求把带敏感数据的URL直接请求到攻击者域名

**重点价值：**

- 用户可能不需要点击链接
- 风险点不只在Agent，也在消息通道默认行为
- 很适合和出站测试结合验证

# 案例5：提示词注入叠加审批绕过与沙箱逃逸

**来源：** [PromptArmor: Snowflake Cortex AI Escapes Sandbox and Executes Malware](https://www.promptarmor.com/resources/snowflake-ai-escapes-sandbox-and-executes-malware)

**基本链路：**

1. 攻击者把恶意指令藏进README或其他不可信上下文
2. Agent被诱导生成危险命令
3. 命令校验只检查表面结构，没有完整理解嵌套表达式
4. 恶意命令绕过批准并在沙箱外执行

**重点价值：**

- 说明“有审批”“有沙箱”不等于真的安全
- 特别适合联动终端过滤与审批模型测试
- 一旦命中，影响通常直接落到执行层

# 案例6：Computer Use产品文档明确提示的注入风险

**来源：** [Anthropic Computer Use Tool Docs](https://platform.claude.com/docs/en/agents-and-tools/tool-use/computer-use-tool)

**关键信息：**

- 登录态任务会放大提示词注入风险
- 网页和图片中的指令可能覆盖原始任务
- 官方建议使用虚拟机、容器、域名白名单与人工确认

**重点价值：**

- 这里反映的不只是单一厂商实现缺陷，还包括产品形态自带风险
- 适合在测试报告里作为“设计层风险”证据
