# MATLAB

## 第一课

### 基础函数

|         **命令**         | **说明**                                |
| :----------------------: | --------------------------------------- |
|       **`clear`**        | 清空 WorkSpace 中的变量                 |
|        **`clc`**         | 清除当前 Matlab 命令窗口的内容（清屏）  |
|        **`pwd`**         | 返回当前路径（print working directory） |
|         **`cd`**         | 修改当前路径（change directory）        |
|       **`mkdir`**        | 新建文件夹（make directory）            |
|       **`rmdir`**        | 删除文件目录（remove directory）        |
|       **`delete`**       | 删除单个文件                            |
|         **`ls`**         | 列出文件与目录（list）                  |
|      **`copyfile`**      | 复制文件或目录，可以重命名              |
|      **`movefile`**      | 移动文件或目录，可以重命名              |
|       **`which`**        | 查找函数或文件位置                      |
|        **`edit`**        | 编辑或创建 m 文件                       |
| **`help 命令/doc 命令`** | 查看命令的帮助/文档                     |

> `which` 命令只会按照MATLAB的搜索路径寻找命令或文件

```matlab

clc;clear;                  % 清空命令行窗口和工作区变量


currentPath = pwd();        % 获取当前文件路径
mkdir('Demo');              % 创建一个新文件夹
ls;                         % 显示当前目录内容
cd('Demo');                 % 进入该文件夹


edit('main_script.m');      % 创建并打开 main_script 



% 将 main_script.m 复制一份并重命名为 backup_script.m
copyfile('main_script.m', 'backup_script.m'); 

% 创建一个专门放备份的子文件夹
mkdir('Backup_Folder');    

 % 将备份文件移动到子文件夹内
movefile('backup_script.m', 'Backup_Folder/'); 


which main_script           % 定位刚才创建的脚本位置
which sin                   % 定位系统内置函数 sin 的位置

cd ('..')                        % 返回文件目录上一级
rmdir('Matlab_Demo_Task', 's');  % 's' 参数表示删除文件夹及其所有子内容

```

### 快捷键（windows 操作系统）

|     **快捷键 **      | **说明**                                     |
| :------------------: | :------------------------------------------- |
|     **Ctrl + R**     | 将选中的多行代码批量注释。                   |
|     **Ctrl + T**     | 取消选中代码块的注释。                       |
|     **Ctrl + I**     | 对多行代码进行智能缩进对齐。                 |
|     **Ctrl + C**     | 在命令窗口可强制退出程序；在编辑器内为复制。 |
|        **F9**        | 仅运行脚本中被选中的部分代码段。             |
|      **Tab 键**      | 在输入时补全变量名、函数名或文件名。         |
| **方向键 “上”/“下”** | 在命令窗口快速找回之前输入过的指令。         |

### m文件命名规则

* 只能包含字母、数字和下划线
* 首字母必须是英文字母
* 不能与MATLAB内部函数同名
* 文件存储路径一定为英文

### 变量命名规则（驼峰体/下划线）

* 只能包含字母、数字和下划线
* 首字母必须是英文字母
* 区分大小写
* 变量名不能超过 `namelengthmax` 

### 简单的矩阵操作

```matlab
% 等差数列
% start:step:stop step可省略，默认为1
a = 1:1:10

% 矩阵操作
data = rand(4, 4) 			% 生成元素属于[0,1]的4x4随机矩阵

a_ij = data(i, j) 			% 取出data中第i行第j列的元素
a_i = data(i, 1:4)  		% = data(i, 1:end) = data(i, :) 取出第i行
a_j = data(1:4, j)			% = data(1:end, j) = data(:, j) 取出第j列
a = data(:[1, 3])			% 取第1列和第3列，取行类似
a = data([2, 4], [2, 4])	% 取多个数

c = [a, b]	% = [a b] 按行拼接矩阵
c = [a; b]	% 按列拼接矩阵
```

### 作业

> 1. 在zuoye目录下建立sub文件夹。
>
> 2. 在sub文件夹内，建立多个子文件夹；这些文件夹以ori文件夹内的pdf编号命名。
> 3. 将ori文件夹内的pdf移动到对应的sub下的文件夹内，并改名为report.pdf。
> 4. 最后删除sub文件夹。

```matlab
% 第一节作业准备工作
clear;clc;

% 创建zuoye/ori（多层级目录）
mkdir('zuoye\ori');  

% 创建所需的pdf文件
for i = 1:10
    f = fopen(sprintf('zuoye\\ori\\0100%02d.pdf',i),"w");
    fclose(f);
end
```

```matlab
clear;clc;
mkdir("zuoye\sub");  % 创建所需文件夹

file_names = ls('zuoye\ori\*.pdf');
file_nos = file_names(:, 1:end-4);   % 获取所有文件编号

for i = 1:length(file_nos)

    no = file_nos(i,:);  % 获取单个文件编号
    mkdir(strcat("zuoye\sub\", no));
    
    % 复制并改名
    ori_path = strcat("zuoye\ori\", file_names(i, :));
    sub_path = strcat("zuoye\sub\", no, "\report.pdf");
    copyfile(ori_path, sub_path);
end
```

```matlab
% 删除sub文件夹
rmdir("zuoye\sub", 's');

% 删除所有文件
rmdir("zuoye", 's');
```



## 第二课

### 常用函数

|    **函数**     | **功能描述**                                                 |
| :-------------: | ------------------------------------------------------------ |
| **`fullfile`**  | 拼接文件或文件夹路径。                                       |
|  **`dir(\*)`**  | 返回指定路径或通配符的文件和文件夹信息。                     |
| **`fileparts`** | 将文件路径拆为三部分：文件夹路径、文件名和扩展名。           |
|   **`find`**    | 返回数组或矩阵中满足条件（或非零）元素的索引。               |
|  **`addpath`**  | 将文件夹临时添加到 MATLAB 的搜索路径中。                     |
|  **`genpath`**  | 生成包含指定文件夹及其所有子文件夹的路径。                   |
|    **`zip`**    | 将文件或文件夹打包压缩为 `.zip` 文件。                       |
|  **`gunzip`**   | 解压缩 `.gz` 格式的压缩文件或目录。                          |
| **`uigetdir`**  | 弹出交互式对话框，供用户浏览并选择文件夹路径。               |
| **`uigetfile`** | 弹出交互式对话框，供用户浏览并选择一个或多个文件。           |
|  **`strcat`**   | 水平拼接多个字符串或字符数组（连接字符数组时会自动忽略尾部空格）。 |

### 矩阵运算

| **函数/符号** | **功能描述**                                             |
| :-----------: | -------------------------------------------------------- |
|    `zeros`    | 创建全零矩阵。                                           |
|    `ones`     | 创建全 1 矩阵。                                          |
|    `rand`     | 创建在 $[0, 1]$ 区间内均匀分布的随机数矩阵。             |
|    `randn`    | 创建符合标准正态分布（均值为 0，方差为 1）的随机数矩阵。 |
|    `size`     | 返回矩阵各维度的长度（行数和列数）。                     |
|   `length`    | 返回向量的长度，或者矩阵中最大维度的长度。               |
|     `sum`     | 对矩阵元素求和（默认按列求和）。                         |
|    `mean`     | 计算矩阵元素的算术平均值（默认按列计算）。               |
|      `'`      | 将矩阵的行和列互换（复数时执行共轭转置）。               |
|     `.*`      | 两个矩阵对应位置的元素相乘。                             |
|      `*`      | 矩阵乘法。                                               |

### 作业

> （本题要求使用交互式的选择路径）
>
> 1. 在ori同级文件夹内，建立pdf文件夹。
> 2. 在pdf文件夹内，建立以pdf文件名命名的文件夹，并放置相应的pdf文件（重命名为report.pdf）
> 3. 压缩pdf文件夹。
> 4. 删除压缩后的文件。

```matlab
% 第二节作业准备工作
clear;clc;

% 创建zuoye/ori（多层级目录）
mkdir('zuoye/ori');  

% 创建所需的文件
file_names = ["010001.docx", "010002.pdf", "010003.xlsx", "010007.pdf", "010008.pptx", "010010.pdf"];

for i = file_names
    f = fopen(fullfile("zuoye/ori/", i),"w");
    fclose(f);
end
```

```matlab
clear;clc;

% 获取 ori 文件夹路径
% ori_path = "D:\matlab_learn\zuoye\ori";
ori_path = uigetdir(".\", "请选择ori文件");
pdf_path = fullfile(ori_path, "..\pdf");

% 建立pdf文件夹
mkdir(pdf_path);

% 提取pdf文件名称
pdf_info = dir(fullfile(ori_path, "*.pdf"));

for i = 1:length(pdf_info)
    name = pdf_info(i).name;
    goal_path = fullfile(pdf_path, name(1:end-4));
    mkdir(goal_path)
    copyfile(fullfile(ori_path, name), fullfile(goal_path, 'report.pdf'))
end

% 压缩pdf文件
zip(pdf_path,pdf_path);
```

```matlab
% 删除pdf.zip文件
delete(fullfile(ori_path, "..\pdf.zip"));

% 删除所有内容
rmdir(fullfile(ori_path, "..\..\zuoye"), 's');
```

> 随机生成一个正态矩阵，矩阵维数为 $3\times5$ ；将所有正数所在的行和列输出出来。用编程语言自动求出矩阵里面元素总数目。

```matlab
clear;clc;

A = randn(3, 5);
[r, l] = find(A > 0);

num = numel(A);
```

> 随机生成一个矩阵，要求数字都位于0-1之间，维数为 $8\times4$ ，求这个矩阵的行方差和列方差。并求矩阵所有元素整体的方差

```matlab
clear;clc;

A = rand(8, 4);
var_r = var(A, 0, 2);
var_l = var(A, 0, 1);
var_all = var(A, 0, 'all')
```

> 随机生成两个 $10\times1$ 的向量，做两个向量之间的双样本t检验，得到p值和t值。

```mysql
clear;clc;

% 生成两个10x1的向量
X = randn(10, 1);
Y = randn(10, 1);
[h, p, ci, stats] = ttest2(X, Y);
```

> 小明同学出生日期是1990年1月20日，请问到2019年12月13日为止，小明多少岁（尽可能精确，岁数可以有小数点）？

```matlab
clear;clc;
t_0 = datetime('1990-01-20');
t_1 = datetime('2019-12-13');

delta_year = year(t_1)-year(t_0);
age = delta_year + years(t_1 - t_0 -years(delta_year));
```



## 第三课

| **函数**        | **功能**                                       |
| --------------- | ---------------------------------------------- |
| **`ind2sub`**   | 将线性索引转换为对应的多维下标（如行、列号）。 |
| **`sub2ind`**   | 将多维下标（如行、列号）转换为线性索引。       |
| **`sort`**      | 对数组元素进行排序（升序或降序）。             |
| **`unique`**    | 找出数组中的唯一值，并按顺序返回。             |
| **`intersect`** | 计算两个集合的交集。                           |
| **`union`**     | 计算两个集合的并集。                           |
| **`setdiff`**   | 计算两个集合的差集。                           |
| **`ismember`**  | 判断数组元素是否为另一个数组的成员。           |
| **`reshape`**   | 在不改变元素总数的情况下，重构数组的维度。     |

### 作业



