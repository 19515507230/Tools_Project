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

### 帮助命令

#### 查询 Git 专属命令

| 命令                                  | 描述                   |
| ------------------------------------- | ---------------------- |
| **`git 命令 -h`**                     | 获取简短的快速参考。   |
| **`git help 命令 / git 命令 --help`** | 获取详细的官方手册页。 |

#### 查询普通的 Bash/Linux 命令

| 命令              | 描述           |
| ----------------- | -------------- |
| **`命令 --help`** | 查看命令的帮助 |
| **`help 命令`**   | 查看命令的帮助 |

### 常用命令

```bash
# 创建本地仓库：Git会在当前目录下创建一个隐藏的文件夹.git
git init

# 查看文件状态
git status

# 工作区(unstaged/untracked) -> 暂存区
git add <文件名>
git add . # .表示所有文件

# 暂存区 —> 本地仓库
git commit -m "注释内容"

# 查看提交日志
git log [option]

# 回退版本
git reset --hard <commit_id>

# 添加文件至忽略列表
```

### git commit 常用参数

| **参数**      | **全称**    | **描述**                                                     |
| ------------- | ----------- | ------------------------------------------------------------ |
| **`-m`**      | `--message` | 指定提交信息。<br />如果不加这个参数，Git 会打开默认编辑器让你输入。 |
| **`-a`**      | `--all`     | 跳过`git add`，直接提交所有已被跟踪（tracked）且被修改或删除的文件。<br />注意：无法提交新创建的文件（untracked files）。 |
| **`-v`**      | `--verbose` | 冗余模式。在编辑器中显示本次提交的具体差异。                 |
| **`--amend`** | N/A         | 撤销/覆盖上次提交。                                          |

### git log 常用参数

| 参数                   | 描述                     |
| ---------------------- | ------------------------ |
| **`--all`**            | 显示所有分支             |
| **`--pretty=oneline`** | 将提交信息显示为一行     |
| **`--abbrev-commit`**  | 使得输出的commitID更简短 |
| **`--graph`**          | 图形显示                 |

### git reset 常用参数

| **模式**         | **移动 HEAD 指针** | **重置暂存区** | **重置工作区** | **安全程度**           |
| ---------------- | ------------------ | -------------- | -------------- | ---------------------- |
| `--soft`         | 是                 | 否             | 否             | 高（保留所有改动）     |
| `--mixed` (默认) | 是                 | 是             | 否             | 中（保留本地文件改动） |
| `--hard`         | 塑造一致性         | 是             | 是             | 低（强制覆盖一切）     |



## 分支

### 常用命令

```bash
# 查看本地分支
git branch

# 创建本地分支
git branch 分支名

# 切换分支
git checkout 分支名

# 创建并切换分支
git checkout -b 分支名

# 合并分支
git merge 分支名

# 删除分支
git branch -d 分支名  # 删除分支时，需要做各种检查
git branch -D 分支名  # 不做任何检查，强制删除
```



## 远程仓库

### SSH 密钥

```bash
# 查看是否存在现有的 SSH 密钥
ls -al ~/.ssh

# 创建新的密钥
ssh-keygen -t ed25519 -C "your_email@example.com"
# -t 指定算法，默认rsa
# -C 指定注释

# 测试连接
ssh -T git@github.com
```

### 远程仓库

```bash
# 关联远程仓库
git remote add <名称> <git@github.com:...>

# 查看关联的远程仓库
git remote

# 推送远程仓库
git push [-f] [--set-upstream] [远端名称] [本地分支名:[远端分支名]]
# 远端分支名和本地分支名相同，可只写本地分支名
# --set-upstream 推送到远端的同时并建立远端分支关联关系
# 当前分支以有关联关系，则可省略远端名称和分支名
```



















