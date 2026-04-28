## 基本配置

### 设置用户信息

```bash
# 设置用户信息
git config --global user.name "harlan"
git config --global user.email "zhangheng203018@outlook.com"

# 查看配置信息
git config --global user.name
git config --global user.email
```

###  常用命令取别名

```bash
# 1. 在用户目录下创建 .bashrc 文件
touch ~/.bashrc

# 2. 在 .bashrc 文件中添加如下内容
# 用于输出git提交日志
alias git-log = 'git log --pretty=online --all --graph --abbrev-commot'
# 用于输出当前目录下文件及基本信息
alias ll='ls -al'
```

### 解决乱码问题

```bash
# 1. 在GitBash中执行
git config --global core.quotepath false

# 2. ${git_home}/etc/bash.bashrc 文件追加下面两行
export LANG="zh_CN.UTF-8"
export LC_ALL="zh_CN.UTF-8"

```

## 操作命令

```bash
# 创建本地仓库：Git会在当前目录下创建一个隐藏的文件夹.git
git init

# 查看文件状态
git statu

# 工作区(unstaged/untracked) -> 暂存区
git add <文件名>
git add . # .表示所有文件

# 暂存区 —> 本地仓库
git commit <文件名>
git commit .




```



