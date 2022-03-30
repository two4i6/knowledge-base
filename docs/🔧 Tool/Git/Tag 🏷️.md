# 标签
- 标签是版本库的一个快照。
- 在发布一个版本时，通常现在版本库中打上一个标签 (tag)，这样就能为一确定打标签时刻的版本。将来取某个标签的版本，就是把那个打标签的历史版本取出来。
- 标签时指向某个commit的指针。


# 创建标签
先切换到打标签的分支上，在使用命令：
```shell
git tag <tagname>
```

*注* 默认的标签是打在最新提交的commit上的，但是也可以给历史提交打上标签:
```shell
git tag <tagname> <commit_id>
```

我们也可以创建带有说明的标签：
```shell
git tag -a v0.1 -m "version 0.1 released" <commit_id>
```
`-a` 指定签名
`-m` 指定文字说明


# 查看标签

## 列出所有标签
```shell
git tag
```
*注* 标签不是时间序而是按字母排序列出的。

## 查看标签信息
```shell
git show <tagname>
```


# 删除标签
```shell
git tag -d <tagname>
```
*注* 因为创建的标签只会存储在本地，不会自动推送到远程。所以打错的标签也可以在本地安全的删除。

## 删除远程标签
需要先删除本地标签，再从远程删除。
```shell
git tag -d <tagname>
git push origin :refs/tags/<tagname>
```


# 推送标签
## 推送某个标签
```shell
git push origin <tagname>
```

## 推送全部标签
```shell
git push origin --tags
```

