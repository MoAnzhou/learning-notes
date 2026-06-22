# [Git] 学习笔记

通过游戏学习：[Git游戏](https://learngitbranching.js.org/?locale=zh_CN)

## 基础操作

+ `git commit`：提交
  + 对前后版本对比，提交差异部分
+ `git branch xxx`：创建分支xxx
  + `git checkout xxx`：切换到xxx分支
    + `git switch`：新版本操作
    + `git checkout -b xxx`：创建新分支同时切换到新分支
+ `git merge xxx`：合并分支
  + 把xxx分支合并到main分支
  + 保留历史，增加一个合并节点
+ `git rebase xxx`：合并分支（复制）
  + 线性复制，会修改提交历史
  + **已经共享给别人使用的提交，不要随意 rebase。**
+ `HEAD`：指向当前分支上最近一次提交记录（哈希值）
  + 分离HEAD：让其指向一个具体的提交，而不是某个分支
+ `git log`：查看提交记录的哈希值
  + 哈希值前几个字符能唯一标识提交记录
+ 相对引用
  + `^`：向上移动1个提交记录
  + `~n`：向上移动n个提交记录
  + `git branch -f xxa xxb`：**强制**移动分支xxa（分支名）到提交记录xxb（哈希值）
+ 撤销变更
  + `git reset HEAD~1`：把分支向上移动
    + **对远程分支无效**
  + `git revert HEAD`：创建新分支，引入更改
+ `git cherry-pick 提交1 提交2 ...`：把节点1、2..复制到当前分支下
+ `-i`：交互式变基
  + `git rebase -i`

---

## 远程操作

+ `git clone`：在本地环境下创建一个远程仓库的拷贝
  + 远程仓库默认`origin`
+ `git fetch`：提交/更新本地仓库
+ `git pull`：从远程仓库提交到本地（上传）
  + `git fetch, git merge o/main`
  + `git pull --rebase`
+ `git push`：从本地上传更新到远程（下载）

---

暂时学这些，应该足够个人使用。团队使用等用到再说吧，记不住啊..