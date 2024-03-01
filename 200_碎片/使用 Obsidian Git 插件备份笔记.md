# 使用 Obsidian Git 插件备份笔记

## 下载安装 Git

[Git - 安装 Git (git-scm.com)](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)

![[Pasted image 20240227223223.png]]

## 在 Github 创建一个私有远程仓库

### 新建一个私有仓库

登录 *github*，点击个人头像进入 *你的仓库/Your repositories*，点击下图中的 *New* 创建一个新的远程仓库。

![[使用 Obsidian Git 插件备份笔记 2024-03-01 15.48.08.excalidraw|1200]]

### 补全名称、配置为私有仓库、自动添加 README

补全仓库名称 *Repository name*、描述 *Description*、设置仓库为私有仓库 *Private*、自动添加 READE 文件 *Add a README file*。创建远程仓库 *Create repository*

![[Pasted image 20240301160103.png]]

## 将仓库克隆到本地、完成配置

在任意路径打开 *cmd*，可以通过在 *文件资源管理器* 的任意路径位置输入 *cmd* 打开。

复制你的远程仓库地址，在 *cmd* 输入命令 `git clone <你的远程仓库地址>` 克隆仓库到本地。如果需要使用 *http 代理* ，输入命令 `git clone -c http.proxy=http://<代理地址>:<代理端口> <你的远程仓库地址>`  

将克隆下的仓库文件夹中的 `.git` 文件夹复制到 *obsidian* 库文件夹中，就完成了配置。

![[使用 Obsidian Git 插件备份笔记 2024-03-01 16.03.01.excalidraw|1200]]

## 使用

![[使用 Obsidian Git 插件备份笔记 2024-03-01 16.31.57.excalidraw|1200]]

配置 `.gitignore` 文件可以设置哪些文件不需要同步到远程仓库，推荐将 `.obsidian` `.trash` 配置到 `.gitignore` 文件中。

```text nums
# to exclude Obsidian's settings (including plugin and hotkey configurations)
.obsidian/

# Add below lines to exclude OS settings and caches
.trash/
.DS_Store

```

用记事本编辑，放在 *obsidian* 的库文件夹中即可

![[Pasted image 20240301163901.png]]

推送完成后，远程库：

![[Pasted image 20240301164149.png]]

关于最后一个 `Git: Pull` 按钮，不熟悉 git 的不建议用，它和 "云端同步到本地" 在逻辑上差别有点大，需要同步到本地时，就直接在 github 上下载吧。