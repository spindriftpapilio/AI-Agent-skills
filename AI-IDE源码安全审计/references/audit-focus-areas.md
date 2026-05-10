# 源码审计重点区域

用于快速定位开源AI IDE中最可能出问题的代码区域。

# 优先搜的函数、能力

### 命令执行

```text

child_process.exec
child_process.execSync
child_process.spawn
child_process.execFile
subprocess.Popen
os.system

```

### 配置读取

```text

settings
config
workspace
rules
instructions
mcp

```

## 信任与审批

```text

trust
approve
allow
permission
sandbox
safe mode

```

## 高风险组合

- 工作区文件内容 ->命令执行
- 工作区配置 ->工具定义 ->自动执行
- 审批结果缓存 ->后续内容变更不重验
- 路径判断 ->符号链接、相对路径、父目录逃逸
