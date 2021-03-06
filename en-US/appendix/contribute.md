---
root: false
name: Contribution of participation
sort: 1
---

加入开源队伍，有同学想加入进来但有些力不从心，其实没有那么复杂。

- 开发
	* 参与代码架构设计
	* 参与BUG修复
	* 参与功能完善
	* 参与性能优化
- 非开发
	* 文档翻译
	* 注释添加

## 如何给开源项目贡献代码

分两种情况：

- 代码仓库管理者给你添加该仓库的写入权限，这样的话可以直接push
- 如果不能直接push（大多数情况），采用经典的fork & pull request来提交代码，下面讲述这种情况

#### fork & pull request

例如有个仓库`https://github.com/biezhi/blade.git`，其采用了经典的分支开发模型，稳定后的代码提交到master分支，其余特性则在dev分支上进行开发，待成熟后合并回master分支。

假如现在需要在其分支3.1.0-dev上提交代码（发现了BUG或者想提交新功能），那么比较简洁的做法如下：

第一步：克隆代码到本地

```
git clone https://github.com/biezhi/blade.git
```

第二步：切换到远程分支3.1.0-dev（远程库默认名字为origin）

```
git checkout origin/3.1.0-dev
```

第三步：基于远程分支3.1.0-dev新建本地分支3.1.0-dev（注意远程分支和本地分支的区别，名字一样，但是一个是远程，一个是本地）

```
git checkout -b 3.1.0-dev

# 也可以这样
git branch 3.1.0-dev
git checkout 3.1.0-dev
```

第四步：在该分支提交你的更改，然后提交

```
git commit -m "fix memory leak bugs"
```

第五步：由于没有直接push到origin的权限，我们需要先对ESUI库进行fork，然后在本地添加一个新的推送地址

```
git remote add upstream git@github.com:biezhi/blade.git
```

第六步：推送本地分支到自己的ESUI fork库（需要先做合并，因为此时远程分支管3.1.0-dev可能合并了其他代码）

```
git fetch origin
git merge origin/3.1.0-dev

git push upstream 3.1.0-dev
```

第七步：这样你的ESUI fork库的3.1.0-dev分支包含了你的最新更改，点击上面的“pull request”就可以推送请求了。注意推送的来源和目的地，如果不对需要点击`Edit`进行修改，另外可以点击下面的标签file changed查看具体的变动，确认无误后填写pull request的标题和具体内容，点击`create pull request`绿色按钮推送就可以了

如果评审人员给出了反馈需要继续修正代码，可以从第六步重新开始，这样所有的提交都会显示到同一个pull request中，如果想发起一个全新的pull request，可以拉出一个新的分支，然后重复第六步开始的工作。

## 贡献开源项目的流程

[http://book.haoduoshipin.com/gitbeijing/fork_flow.html](http://book.haoduoshipin.com/gitbeijing/fork_flow.html)

