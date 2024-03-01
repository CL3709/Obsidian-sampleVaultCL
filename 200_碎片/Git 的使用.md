# Git 是什么

>[!note] Git 是目前世界上最先进的分布式版本控制系统。

## 工作原理/流程

![[v2-3bc9d5f2c49a713c776e69676d7d56c5_720w.png]]

- Workspace: 工作区
- Index/Stage: 暂存区
- Repository: 仓库区
- Remote: 远程仓库

## SVN 和 Git 的主要区别

SVN 是集中式版本控制系统，版本库是集中放在中央服务器的，而干活的时候，用的都是自己的电脑，所以首先要从中央服务器哪里得到最新的版本，然后干活，干完后，需要把自己做完的活推送到中央服务器。集中式版本控制系统是必须联网才能工作，如果在局域网还可以，带宽够大，速度够快，如果在互联网下，如果网速慢的话，就纳闷了。

Git 是分布式版本控制系统，那么它就没有中央服务器的，每个人的电脑就是一个完整的版本库，这样，工作的时候就不需要联网了，因为版本都是在自己的电脑上。既然每个人的电脑都有一个完整的版本库，那多个人如何协作呢？比如说自己在电脑上改了文件 A，其他人也在电脑上改了文件 A，这时，你们两之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。

# 在 Windows 上安装 Git

>[!Note] 下载链接
> [Git - Downloading Package](https://git-scm.com/download/win)

安装完成后可以找到 Git Bash，需要完成最后一步设置，在 git bash 中输入：

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 ~
$ git config --global user.name "raven370"

hyxin@LAPTOP-0E60G5SM MINGW64 ~
$ git config --global user.email "obsidian@ob.com"

hyxin@LAPTOP-0E60G5SM MINGW64 ~
$

```

因为 Git 是分布式的版本控制系统，所以需要填写用户名和邮箱作为一个标识。

>[!Tip] 注意
>Git config --global 参数，表示这台机器上所有的 git 仓库都会使用这个配置，如果对某个仓库需要指定不同的用户命令和邮箱，也可以单独配置。

# 如何操作

## 创建版本库

>[!abstract] 什么是版本库？
>Repository，可以简单的理解为一个目录，目录里所有的文件的都可以被 git 管理起来，每个文件的修改，删除，git 都能跟踪，以便在任何时刻都可以追踪历史，或者在将来的某个时刻将文件还原到历史版本。

创建第一个版本库，只需要选择一个目录执行命令 `git init` 即可

```shell
# 通过git init命令将目录变成git可以管理的仓库

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository
$ pwd
/d/GitRepository

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository
$ mkdir testgit

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository
$ cd testgit/

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit
$ git init
Initialized empty Git repository in D:/GitRepository/testgit/.git/

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$

```

>[!warning] 注意
>此时 testgit 目录下会多出一个 `.git` 目录，这个目录是 git 用于管理跟踪版本的，如果修改，可能会破坏 git 仓库。

```bash
$ ls -al
total 4
drwxr-xr-x 1 hyxin 197121 0 Aug 26 18:47 ./
drwxr-xr-x 1 hyxin 197121 0 Aug 26 18:47 ../
drwxr-xr-x 1 hyxin 197121 0 Aug 26 18:47 .git/
```

## 将文件添加至版本库，并提交到分支

>[!tip] 注意
>所有的版本控制系统，都只能跟踪<mark class="hltr-orange">文本文件</mark>的改动，如 txt、html、代码文件等，git 也是一样，版本控制系统可以清楚的告知每次的改动。对于图片，视频等<mark class="hltr-red">二进制文件</mark>，虽然也能由 git 管理，但是无法跟踪文件变化，比如文件大小的改动可以明确，但具体内容的改动是无法跟踪的。

### demo 演示

以下是一个简单的 demo 演示：

1. 在 testgit 目录下（暂存区），新建一个 `readme.txt` ，使用命令 `git add readme.txt` 将文件 `readme.txt` 添加到暂存区（仓库目录下）

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ echo "hello world" > readme.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git add readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

```

>[!info] 上面的警告常常在 windows 出现
>这个警告是指在 Git 版本控制系统中，文件 `readme.txt` 的<mark class="hltr-orange">行尾换行符（Line Feed，LF）</mark>将会在下一次 Git 操作时被换成<mark class="hltr-red">回车符加换行符（Carriage Return Line Feed，CRLF）</mark>。这种警告通常出现在 Windows 操作系统中，因为在 Windows 上，文本文件的行尾通常使用 CRLF 表示换行，而在类 Unix 系统（如 Linux 和 macOS）中，通常使用 LF 表示换行。这个警告意味着在不同的操作系统间协作时，Git 将自动调整换行符以保持一致性。

2. 用命令 git commit 提交文件到仓库

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git commit -m 'readme.txt提交'
[master (root-commit) b605b1e] readme.txt提交
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt

```

>[!info] `-m` 参数后的字符串为提交的注释

3. 现在已经提交了 `readme.txt` 文件了，我们可以通过 `git status` 命令来查看，暂存区中是否还有未提交的文件

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git status
On branch master
nothing to commit, working tree clean

```

>[!info] 这个回显提示，在 branch master 分支下，没有未提交的内容了

4. 现在继续修改 `readme.txt` 的内容，添加一些文件内容，再使用 `git status` 查看下结果

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ echo "add something" >> readme.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")

```

>[!info] 这个回显提示 `readme.txt` 的文件内容被修改了

5. 想要查看具体被修改的内容，使用 `git diff` 命令

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git diff readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it
diff --git a/readme.txt b/readme.txt
index 3b18e51..6d05489 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1 +1,2 @@
 hello world
+add something

```

>[!info] 可以看到，文件增加了一行 add something

6. 现在，我们知道了 `readme.txt` 文件具体做了什么样的修改，这时可以放心的将它提交到仓库了，提交修改和提交文件一样，有两个步骤，先是 `git add` 然后 `git commit`

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git add readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   readme.txt


hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git commit -m "readme.txt增加行add something"
[master a0ab74c] readme.txt增加行add something
 1 file changed, 1 insertion(+)

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git status
On branch master
nothing to commit, working tree clean

```

>[!info] commit 之前、之后，都可以用 status 确认下状态

7. 经过上述的操作，我们已经学会如何修改文件了，现在继续修改文件，增加一行 bad content，将其提交，现在我们已经对 `readme.txt` 文件做了三次修改了，想要进行历史记录的查询，使用 `git log` 命令

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ echo "bad content" >> readme.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git add readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git commit -m "readme.txt增加bad content"
[master a3403d9] readme.txt增加bad content
 1 file changed, 1 insertion(+)

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git log
commit a3403d97972ae5da997ddd2e7a4a06f1845fb5cc (HEAD -> master)
Author: raven370 <obsidian@ob.com>
Date:   Sat Aug 26 22:33:12 2023 +0800

    readme.txt增加bad content

commit a0ab74c704101a27d64d1358884c9861ebdc5d83
Author: raven370 <obsidian@ob.com>
Date:   Sat Aug 26 22:26:55 2023 +0800

    readme.txt增加行add something

commit b605b1e97d789f296411d389c1ce76be3668997d
Author: raven370 <obsidian@ob.com>
Date:   Sat Aug 26 22:12:30 2023 +0800

    readme.txt提交

```

>[!info] `git log` 命令显示从最近到最远的日志，commit 后面的随机字串，是每次提交的版本号，从注释可以看出，上一次的提交内容是"`readme.txt` 增加 bad content"
>如果嫌 `git log` 命令显示的内容过多的话，我们可以使用 `git log -pretty=oneline` 命令

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git log --pretty=oneline
a3403d97972ae5da997ddd2e7a4a06f1845fb5cc (HEAD -> master) readme.txt增加bad content
a0ab74c704101a27d64d1358884c9861ebdc5d83 readme.txt增加行add something
b605b1e97d789f296411d389c1ce76be3668997d readme.txt提交

```

8. 现在，我想使用版本回退操作，将当前版本回退到上一个版本，可以使用如下两种命令：
	1. `git reset --hard HEAD^` 如果要回退到上上个版本则是 `git reset --hard HEAD^^`
	2. 如果要回退很多版本，比如回退 100 个版本，可以用 `git reset --hard HEAD~100`

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ cat readme.txt
hello world
add something
bad content

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git reset --hard HEAD^
HEAD is now at a0ab74c readme.txt增加行add something

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ cat readme.txt
hello world
add something

```

9. 经过上面的操作，可以看到 bad content 的内容已经消失了，但是如果我们用 `git log` 命令查看，也会发现增加 bad content 内容的版本消失了，那如果要回退到最新的版本，要怎么做呢？这里需要用到 `git reset --hard 版本号` 进行回退，我们可以通过命令 `git reflog` 来获取到全部的版本号。

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git log
commit a0ab74c704101a27d64d1358884c9861ebdc5d83 (HEAD -> master)
Author: raven370 <obsidian@ob.com>
Date:   Sat Aug 26 22:26:55 2023 +0800

    readme.txt增加行add something

commit b605b1e97d789f296411d389c1ce76be3668997d
Author: raven370 <obsidian@ob.com>
Date:   Sat Aug 26 22:12:30 2023 +0800

    readme.txt提交

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git reflog
a0ab74c (HEAD -> master) HEAD@{0}: reset: moving to HEAD^
a3403d9 HEAD@{1}: commit: readme.txt增加bad content
a0ab74c (HEAD -> master) HEAD@{2}: commit: readme.txt增加行add something
b605b1e HEAD@{3}: commit (initial): readme.txt提交

```

>[!tip] 可以看到增加 bad content 内容的版本号是 `a3403d9`
>用 `git reset --hard 版本号` 命令来恢复吧
>

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git reset --hard a3403d9
HEAD is now at a3403d9 readme.txt增加bad content

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ cat readme.txt
hello world
add something
bad content

```

>[!info] 可以看到，`readme.txt` 回到了最新的版本

## 工作区与暂存区的区别

### 工作区

从上面的 demo 来看，工作区就是电脑上看到的，经过过 git init 的目录，即 testgit 目录里的文件。

### 版本库（Repository）

工作区中有一个隐藏目录 `.git`，这个目录不属于工作区，称为版本库。版本库中存储了很多东西，最重要的就是 stage （暂存区），看上文的 demo 的话，<mark class="hltr-orange">则还有 git 为我们自动创建的第一个分支 master，以及指向 master 的一个指针 HEAD</mark>。

git 提交文件有两个步骤，`git add` 就是将文件提交到暂存区`git commit` 则是将暂存区中的<mark class="hltr-red">所有内容</mark>提交到当前分支。

### 继续使用上一个 demo 进行演示说明

1. 现在我们在 `readme.txt` 文件中再添加一行内容 stage test，接着在目录下新建文件内容为 test 的 `test.txt`，使用 `git status` 命令查看下状态

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ echo "stage test" >> readme.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ echo "test" > test.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test.txt

no changes added to commit (use "git add" and/or "git commit -a")

```

>[!info] 可以看到 git 记录了我们在工作区的变更

2. 现在我们先使用 `git add` 命令，将两个文件都添加到暂存区，再使用 `git status` 命令看下状态。

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git add readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git add test.txt
warning: in the working copy of 'test.txt', LF will be replaced by CRLF the next time Git touches it

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   readme.txt
        new file:   test.txt

```

接着，我们可以使用 `git commit` 一次性提交到分支上

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git commit -m "一次性提交readme.txt的文件修改和新增的文件test.txt"
[master 0696ffe] 一次性提交readme.txt的文件修改和新增的文件test.txt
 2 files changed, 2 insertions(+)
 create mode 100644 test.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git status
On branch master
nothing to commit, working tree clean

```

## git 撤销修改和删除文件操作

### 撤销修改

现在我向 `readme.txt` 文件中添加了内容 missing，在我<mark class="hltr-orange">未提交之前</mark>，我发现这个内容有问题，所以我得马上恢复到之前的版本，从上文学到的内容，我们有两种方法。

- 第一，如果我知道我需要删除的内容，我可以在工作区直接手动删去文件中的内容，再 add 到暂存区，然后 commit
- 第二，我可以使用 `git reset --hard HEAD^` 直接回退到上一个版本

但是我不想用上面的两种方法，是否可以直接在工作区中撤销这个修改呢？其实从 demo 演示中，以及可以找到答案了，我们先用 `git status` 确认下状态

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ cat readme.txt
hello world
add something
bad content
stage test
missing

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")

```

>[!tip] git 的回显已经提示了撤销操作
>从回显可以看出，使用 `git restore <file>` 命令可以丢弃工作区的修改，尝试下

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git restore readme.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ cat readme.txt
hello world
add something
bad content
stage test

```

>[!info] 内容 missing 没有了
> `git restore readme.txt` 命令的意思，就是把 `readme.txt` 文件在工作区中所做的修改全部撤销，这里有两种情况:
> 1. `readme.txt` 文件自动修改后，还没有放到暂存区，使用撤销修改，会回到和版本库一模一样的状态
> 2. 另外一种是 `readme.txt` 文件已经放入到暂存区了，接着又做了修改，这时撤销修改，会回到添加暂存区后的状态

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ echo "stage restore test" >> readme.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git add readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ echo "missing" >> readme.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ cat readme.txt
hello world
add something
bad content
stage test
stage restore test
missing

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git restore readme.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ cat readme.txt
hello world
add something
bad content
stage test
stage restore test

```

### 删除文件

现在添加文件 `b.txt` 然后提交它，再删除 `b.txt` 和 `test.txt`，用 `git status` 查看下状态

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ echo "b" > b.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git add b.txt
warning: in the working copy of 'b.txt', LF will be replaced by CRLF the next time Git touches it

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git commit b.txt -m "commit new txt file b.txt"
warning: in the working copy of 'b.txt', LF will be replaced by CRLF the next time Git touches it
[master 0b5a6ae] commit new txt file b.txt
 1 file changed, 1 insertion(+)
 create mode 100644 b.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ rm b.txt test.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   readme.txt

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    b.txt
        deleted:    test.txt

```

>[!info] 可以看到两个文件已经被删除了
>现在有两个选择，一是直接 commit 掉，二是从版本库中恢复被删除的文件；同样的，根据提示，我们可以使用 `git restore` 命令进行恢复

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git restore b.txt test.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ ls
b.txt  readme.txt  test.txt

```

>[!info] 可以看到两个文件回来了

# 远程仓库和分支管理

一般来说，常见的是 github，文中的演示也都以 github 为例。

## Github 基本连接配置

本地 git 仓库和 github 仓库之间的传输选择 SSH 的方式，如果使用这种方式，需要配置免密。

在 git bash 里，配置免密的方法和 linux 相同。通过 `ssh-keygen` 命令配置。

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ cd

hyxin@LAPTOP-0E60G5SM MINGW64 ~
$ ssh-keygen.exe -t rsa -C "obsidian@ob.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/hyxin/.ssh/id_rsa):
/c/Users/hyxin/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/hyxin/.ssh/id_rsa
Your public key has been saved in /c/Users/hyxin/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:/pmIXOKlltxJGlhbHp6Bse4LGmMmdP7Pw+hmJRRbLrI obsidian@ob.com
The key's randomart image is:
+---[RSA 3072]----+
|                 |
|     ...         |
|      =+         |
|   . ++.+        |
| . .++.=S+       |
|. oE..+o=        |
|. =..o**+.       |
| + +.BBOoo o     |
|  . ++B+o +      |
+----[SHA256]-----+

hyxin@LAPTOP-0E60G5SM MINGW64 ~
$ ls .ssh/
config  id_rsa  id_rsa.pub  known_hosts  known_hosts.old

hyxin@LAPTOP-0E60G5SM MINGW64 ~
$ cat .ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC2MOr8BJ3rw+GzW3Yrrcu/T/mfHR2YDnCdVNrs20SuG8OUyepE29vfmr1Bf/P5hNY537yDFJTJbyvQK5wUHrQ3nrd2ViRKhKWa0vIP041RE0YRGJsv9OxkWcW8UtkaywW2Ym+V5FY8Okx9xRfIYLKn7emzKPduaWM/5IufvYq0Hb34JUKlnurWr7NJ+uDVdTVPsDH0xX59gouYFecSzYhBh2fmCaajLZszRHpxmUJ65wwCv/6aImsV8lsEd4/WqbK3r14663olXnpuhC2PpGVeqJZ6JCpLwuMdklGxwiMSCGli+EgiZZfdg2B3czMqLg2PMGrYI03FgHSiGpDnumWdW1Sk2bVlR4dnLBXilAXM4gIt+17yTfLQq+nuL+uCKwOCeY/1eOxbzme/740IcVBelp166K3hqiYQ6q+FNoT1jhoOlYZ+pqwSGgLYNVAbZCgxX8+NiNY4pNdt/BB/8tdmu30bJAlDo6bMGC6Yp2q8x5lprgVwmIsjjd6674tigUk= obsidian@ob.com

```

>[!warning] 私钥
> `id_rsa` 为私钥，不能泄露。`id_rsa.pub` 是公钥，可以放心的告诉任何人

接下来登录 github，在设置页面中的 SSH and GPG keys 选择 add new SSH Key。Title 任意填写，Key type 就用默认的 Authentication Key。将自己的公钥 `id_rsa.pub` 填写到 Key，点击 Add SSH key 确认添加。

![[Pasted image 20230827102822.png]]

## 添加一个远程仓库

现在的情景是，我们已经在本地拥有了一个 git 仓库 gittest，现在又想在 github 创建一个 git 仓库，并且希望这两个仓库能够进行远程同步。这样 github 仓库可以作为云端备份，又允许其他人通过该仓库来协作。

首先，登录 github，在右上角找到 create a new repo 创建一个新的仓库。

![[Pasted image 20230827103547.png]]

创建好之后，github 的引导页面也会告诉我们，这个 testgit 仓库是空的，可以从这个仓库克隆出新的本地仓库，也可以把一个已有的本地仓库与之关联，然后把本地仓库的内容推送到 github 仓库。

现在，我们根据 github 的提示来操作。

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 ~
$ cd -
/d/GitRepository/testgit

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git remote add origin git@github.com:RuAn370/testgit.git

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git push -u origin master
Enumerating objects: 16, done.
Counting objects: 100% (16/16), done.
Delta compression using up to 20 threads
Compressing objects: 100% (7/7), done.
Writing objects: 100% (16/16), 1.35 KiB | 1.35 MiB/s, done.
Total 16 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:RuAn370/testgit.git
 * [new branch]      master -> master
branch 'master' set up to track 'origin/master'.

```

>[!warning] 注意
>这里，github 官方的引导是将本地仓库分支 main 的内容推送到了远程仓库。而我这边是将分支 master 的内容推送到了远程仓库。
>
>同时，由于远程仓库是空的，我们第一次推送 master 分支时，加上了 `-u` 参数，git 不但会把本地 master 分支内容推送到远程仓库的新的 master 分支，还会把本地的 master 分支和远程的 master 分支关联起来，在以后的推送或者拉取时，就可以简化命令。

这时，在 github 页面上就可以看到，远程库的内容已经和我们的本地库完全相同了。

![[Pasted image 20230827104749.png]]

>[!tip] 后续简化的推送命令
>从现在起，只要本地做了提交，就可以通过命令 `git push origin master` ，将本地 master 分支的最新修改推送到 github 上了，从现在开始，testgit 已经正式成为一个分布式版本库了。

## 从远程仓库克隆

上面我们已经学会，在现有本地库，后有远程库时，如何关联远程库。假如远程库有了新的内容，想要克隆到本地上，可以使用 `git clone 远程仓库地址` 命令。

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ cd ..

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository
$ mkdir clonetest

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository
$ cd clonetest/

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/clonetest
$ git clone https://github.com/RuAn370/testgit.git
Cloning into 'testgit'...
remote: Enumerating objects: 16, done.
remote: Counting objects: 100% (16/16), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 16 (delta 0), reused 16 (delta 0), pack-reused 0
Receiving objects: 100% (16/16), done.

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/clonetest
$ ls
testgit/

```

## 创建与合并分支

在版本回退的学习里，我们已经知道，git 会把每次提交串成一条时间线，这条时间线就是一个分支。截止到目前，我们的 testgit 版本库里，只有一条时间线，也就是 master 分支。HEAD 则是指向 master 分支的指针。

但是，HEAD 作为一个指针，如果还有其他的分支存在，自然可以指向不同的分支。

首先，我们来创建 dev 分支，然后切换到 dev 分支上。

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git checkout -b dev
Switched to a new branch 'dev'

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (dev)
$ git branch
* dev
  master

```

>[!tip] `git checkout -b dev`
>这条命令相当于连续执行两条命令：先执行 `git branch dev` 后执行 `git checkout dev`

通过 `git branch` 查看分支，会列出所有分支，当前分支页面会添加一个星号。

我们现在在 dev 分支上继续做 demo，给 `readme.txt` 添加一些内容然后提交。

```
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (dev)
$ cat readme.txt
hello world
add something
bad content
stage test
stage restore test

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (dev)
$ echo "dev branch content add test" >> readme.txt

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (dev)
$ git add readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (dev)
$ git commit -m "dev branch add content"
[dev e4f17cf] dev branch add content
 1 file changed, 2 insertions(+)

```

现在 dev 分支的工作已经完成，我们切换到 master 分支上，继续查看 `readme.txt` 文件的内容。

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (dev)
$ git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ cat readme.txt
hello world
add something
bad content
stage test

```

可以看到 dev 分支上的修改对于 master 分支并没有影响。

现在我们在 dev 分支上，已经确认了自己的修改没有任何问题，那么我们希望将 dev 分支修改的内容合并到 master 分支上，而不是手动去修改和提交。可以使用 `git merge dev` 命令。

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git merge dev
Updating 0b5a6ae..e4f17cf
Fast-forward
 readme.txt | 2 ++
 1 file changed, 2 insertions(+)

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ cat readme.txt
hello world
add something
bad content
stage test
stage restore test
dev branch content add test

```

>[!tip] 提示
>Git merge dev 命令将分支 dev 合并到当前分支，执行合并时，要确认当前分支是哪个。
>
>注意到了 Fast-forward 信息，这个信息是 git 的提示，说明这次的合并是"快进模式"，即直接将 master 指向 dev的当前提交，所以合并速度非常快。

合并完成后，我们就可以删除掉不用的 dev 分支了

```shell
hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git branch -d dev
Deleted branch dev (was e4f17cf).

hyxin@LAPTOP-0E60G5SM MINGW64 /d/GitRepository/testgit (master)
$ git branch
* master

```

# reference

[Git使用教程,最详细，最傻瓜，最浅显，真正手把手教 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/30044692)

[[Git Cheat List]]
