# Python install manager

### Python安装

```bash
# 查看已安装版本
py list

# 查看已安装版本及安装路径
py --list-paths

# 安装指定版本
py install <tags>

# 查看默认运行版本
py --version

# 查看指定版本所安装的库
py -<tags> -m pip list

# 给指定版本安装库
py -<tags> -m pip install 库名
py -<tags> -m pip install 库名 -i https://pypi.tuna.tsinghua.edu.cn/simple

# 给指定版本卸载库
py -<tags> -m pip uninstall 库名
```

### 虚拟环境

```bash
# 查看已安装的python版本
py list

# 查看可安装的python版本
py list --online

# 安装最新的3.14
# py install <tags>
py install 3.14

# 创建虚拟环境
cd <项目路径>

# 创建虚拟环境
py-<tags> -m venv .venv

# 更新pip
.\.venv\Scripts\python.exe -m pip install --upgrade pip

# 向虚拟环境中安装第三方库（不激活的方式）
.\.venv\Scripts\python.exe -m pip install <第三方库>

# 查看虚拟环境中已安装的第三方库
.\.venv\Scripts\python.exe -m pip list
```

