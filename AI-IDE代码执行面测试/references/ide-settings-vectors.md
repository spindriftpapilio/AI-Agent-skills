# IDE设置滥用向量

核心思路：通过工作区级设置文件，把IDE指向攻击者准备的可执行文件。

**参考来源：** [IDEaster](https://maccarita.com/posts/idesaster/)

# VS Code：`php.validate.executablePath`

**触发模型：**

- 工作区中有`.php`文件时，通常很容易被触发

**常用步骤：**
1. 准备恶意或测试用可执行文件
2. 写入`.vscode/settings.json`
3. 把`php.validate.executablePath`指向该文件
4. 打开或切换PHP文件，观察是否调用

# 其他同类设置

留意这些把路径交给外部程序的字段：

- 解释器路径
- 校验器路径
- 格式化器路径
- 终端Shell路径
- 自定义task或command runner

# 判断标准

- 是否工作区级可控
- 是否自动生效
- 是否有审批
- 审批是否会绑定内容
