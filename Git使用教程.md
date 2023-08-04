# Git使用教程

## 一、配置

### 一、基本命令简介

1. clone:克隆，从远程仓库克隆代码带本地仓库
2. checkout:检出，从本地仓库检出一个仓库分支然后进行修订
3. add：添加，在提交前先将代码提交到暂存区
4. commit:提交，提交到本地仓库，本地仓库中保存修改的各个历史版本
5. fetch:抓取，从远程库，抓取到本地仓库，不进行任何合并动作，一般操作较少
6. pull:拉取，从远程库拉到本地库，自动进行合并，然后放到工作区，相当于fetch+merge
7. push:推送，修改完成后，需要和团队成员共享代码时，将代码推送到远程仓库

### 二、配置

#### 一、设置和查看用户信息

1. git.cofig --global user.name "xxx"
2. gi config --global user.email "xx@xx.com"
3. 查看信息不加后缀字符

## 二、常用命令

### 一、获取本地仓库

1. 创建一个空目录作为本地GIT仓库
2. 进入目录，点击右键打开Git bash
3. 执行命令git init
4. 创建成功可以看到隐藏的.git文件

### 二、基础操作指令

Git中存在工作区，暂存区，仓库三个地方。

git add 文件名 ： 将文件从工作区添加到仓库区

git commit ：将文件从暂存区添加到本地仓库

git status ：查看修改的状态，是暂存区还是在工作区

git log: 查看提交日志

​	--all: 显示所有分支

​	--graph: 以图的形式显示

git reset --hard commitID: 版本切换,commitID可以使用git log查看

git reflog: 查看已经删除的提交记录·

忽略部分文件

```bash
# dir 不需要提交的目录
/node_modules

# file 不需要提交的文件
config.ini

# log 不需要提交的任意包含后缀名为log的文件
*.log

# Package Files 不需要提交的任意包含后缀名为jar的文件
*.jar
```

### 三、分支

分支将开发从主线分离，以免影响主线开发。

git branch : 查看本地分支

git branch 分支名 ：创建本地分支

git checkout 分支名：切换并创建分支

git merge 分支名：一个分支上的提交合并到另一个分支

git branch -d ：删除分支, -D 强制删除

解决分支冲突：同时修改了同一文件同一地方，手动解决

开发中分支使用原则：

- master分支：线上分支，主分支
- develop分支：开发分支
- feature分支：从develop创建的分支，一般是同期并行开发，但不同时期上线时创建的分支
- hotfix分支：从master派生的分支，一般作为线上bug修复使用，修复完成后合并到其他分支。

### 四、远程仓库

1. 配置SSH公钥

   ssh-keygen -t rsa：生成公钥，如果已经存在则覆盖

2. 获取公钥

   cat -/.ssh/id_rsa.pub

3. 验证配置

   ssh -T git@github.com

4. 添加远程仓库

   git remote add 远端名称 仓库路径

   远端名称默认为origin，仓库路径从服务器获取URL，如https://github.com/plancan/test.git。

   git remote：查看远程仓库

5. 推送到远程仓库

   git branch --set-upstream-to=origin/远程分支的名字 本地分支的名字：建立关联

   git push [-f] [--set-upstream] 远端名称 本地分支名：远端分支名

   如果远程分支名和本地分支名相同，则只写本地分支。

   - git push origin master

   --set-upstream推送到远端的同时并且建立和远端分支的关联关系

   如果当前分支和远端分支关联，则可以省略分支名和远端名

   - git push

6. 从远端仓库克隆

   如果已经有一个远端仓库，我们可以直接clone到本地

   git clone

7. 从远程仓库抓取和拉取

   远程分支和本地分支一样，我们可以进行merge操作，只是需要先把远端仓库更新都下载到本地，在进行操作。

   - 抓取：：git fetch remote name branch nema

     抓取就是把仓库的更新都抓到本地，不会进行合并，如果不指定远端名称和分支名，则抓取所有分支。

   - 拉取：git pull remote name branch name

     拉取指令就是将远端仓库修改拉到本地自带进行合并，等于fetch+merge，如不指定名称，拉取所有分支。

8. 解决合并冲突

   一段时间，不同用户修改了同一文件同一位置，发生合并冲突。解决方法同本地

### 五、IDEA使用Git

1. 配置Git
