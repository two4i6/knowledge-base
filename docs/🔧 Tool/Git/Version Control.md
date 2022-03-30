# 版本控制
时光机

## 退回版本
在Git中 `HEAD` 是指向版本的指针 
- `HEAD` 表示当前版本。
- `HEAD^` 表示上一个版本。
- `HEAD^^` 表示上上一个版本。
- `HEAD~100` 表示往上100个版本。

退回上个版本有两种方法：
- `reset` 用于退回版本，可以遗弃不在使用的提交。
- `revert` 在当前提交后面，新增一次提交，抵消掉上一次提交所导致的所有变化，不会改变过去的历史，用于安全的取消过去发布的提交。

### Rest
`git reset —hard <commit_id>`
![[B637F488-E751-4E1A-B65C-1B4E3197E3CC.png]]
如果将指针移动到上一个版本：
```shell
git reset --hard HEAD^
```

如果想反悔了可以使用 `git reset —hard <commit id>` 将指针移动到指定的版本： 
```shell
git reset --hard 1094a
```
- `--mixed`  (默认)， 只有暂存区变化。
- `--hard` 暂存区和工作区都会发生变化。 
- `--soft` 暂存区和工作区都不会发生变化。

### Revert
`git revert <commit_id>`
![[B74AF672-5E55-42EA-AA93-1A7441F05AA6.png]]

如果是撤销前一个版本：
```shell
git revert HEAD
```


## 在提交之前撤销
在提交前撤销修改， 使用 `checkout` 命令撤销修改。
`git checkout — <file>` 
- 如果 `<file>` 没有放入暂存区，撤销修改回到和版本库一样的状态。
- 如果 `<file>` 已经放入暂存区，撤销修改回到添加到暂存区后的状态。
总之就是让文件恢复到最后一次 `git commit` 或 `git add` 时的状态。

```shell
git checkout -- readme.md 
```
**注意** `--` 十分重要，如果没有 `--` 则变成了切换到另一个分支的命令。


##  找回删除的文件
同样使用 `git checkout -- <file>`
`git checkout`  其实是用版本库 / 暂存区里的版本替换工作区的版本。

``` shell
git checkout -- readme.md
```
