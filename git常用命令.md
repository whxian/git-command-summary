# git常用命令

+ 查看本地分支：`git branch`
+ 查看远程分支：`git branch -r`
+ 查看本地+远程分支：`git branch -a`
+ 关联本地分支和远程分支：`git branch --set-upstream-to=origin/<originBranchName> <currentBranchName>`
+ 查看最近一次提交的版本号及commit：`git branch -v`
+ 查看近三次提交的版本号及commit：`git branch -vv`
+ 合并指定分支到当前分支：`git merge <branchName>`
+ 删除本地分支：`git branch -d <branchName>`
+ 删除远程分支：`git push -d origin <branchName>`
+ 在本地删除远程已经不存在的分支：`git fetch -p`
+ 重命名分支：`git branch -m <oldBranchName> <newBranchName>`
+ 将远程git仓库里的指定分支拉取到本地(本地不存在的分支)：`git checkout -b 本地分支名 origin/远程分支名`
+ 将远程git仓库里的指定分支拉取到本地(本地会创建出与远程分支同名的分支)：`git checkout --track origin/远程分支名`
+ 从远程仓库获取所有分支：

```
  git branch -r | grep -v '\->' | while read remote; do git branch --track "${remote#origin/}" "$remote"; done
  git fetch --all
  git pull --all
```

- 撤销所有本地修改：`git checkout . `

- 新建分支并且切换到该分支：`git checkout -b <branchName>`

  > 相当于下面两条命令的合并

  1. 新建分支：`git branch <branchName>`

  2. 切换另一分支：`git checkout <branchName>`

- 撤销单个文件修改：`git checkout -- <fileName>`

- 撤销某个add：`git reset HEAD <fileName>`

- `git fetach`与`git pull`的区别:

  > 1. `git fetch `相当于是从远程获取最新到本地，不会自动merge，如下指令：
  >
  > ```git
  > //方法一
  > git fetch origin master		//从远程的origin仓库的master分支下载代码到本地的origin master
  > 
  > git log -p master.. origin/master	//比较本地的仓库和远程参考的区别
  > 
  > git merge origin/master 	//把远程下载下来的代码合并到本地仓库，远程的和本地的合并
  > 
  > //方法二
  > git fetch origin master:temp	//从远程的origin仓库的master分支下载到本地并新建一个分支temp
  > 
  > git diff temp	//比较master分支和temp分支的不同
  > 
  > git merge temp	//合并temp分支到master分支
  > 
  > git branch -d temp	//删除temp
  > ```
  >
  > 2. `git pull`相当于是从远程获取最新版本并merge到本地
  >
  > ```git
  > git pull origin master
  > ```
  >
  >

- 修改commit注释：`git commit --amend`

- 写多行commit注释：

  ```
  git commit -m '
  1. line one
  2.line two
  '
  ```

- 添加到暂存区并提交：`git commit -a -m "commit注释"` = `git commit -am "commit注释"`

  > 相当于下面两条命令的合并

  1. 添加到暂存区：`git add .`
  2. 添加到缓存区：`git commit -m "commit注释"`

- 回退到某个版本：`git reset --hard <版本号>`

- 删除最后一次push并且不保留本地修改：`git reset --hard HEAD^`

- 撤销commit但保留本地修改：`git reser --soft HEAD^`

  > 如果是上一个版本，也可以写成HEAD~1 = HEAD^
  >
  > 如果你进行了2次commit，想都撤回，可以使用HEAD~2 = HEAD^^

  > **至于这几个参数：**
  > `--mixed `
  > 不删除工作空间改动代码，撤销commit，并且撤销`git add . `操作
  > 这个为默认参数，`git reset --mixed HEAD^ `和 `git reset HEAD^` 效果是一样的
  >
  > `--soft  `
  > 不删除工作空间改动代码，撤销commit，不撤销`git add `
  >
  > `--hard`
  > 删除工作空间改动代码，撤销commit，撤销`git add `

- 查看提交历史：`git log`（显示近几次提交的详细历史）

  > 多屏显示控制方式： 空格向下翻页 、b 向上翻页 、q 退出

  > - 将每条log单行输出并显示剪短的版本号：`git log --oneline`
  >
  > - 将每条log单行输出并显示完整的版本号：`git log --pretty=oneline`
  >
  > - 指定log显示条数：`git log --online -[length]`
  >
  > - 显示log的更多改动记录包括修改文件及修改内容：`git log -1 -p`

- 查看所有分支的所有操作记录：`git log`（包括已经被删除的 commit 记录和 reset 的操作）

---

**git中一些选项解释**

1. **-d**  --delete：删除
2. **-D**  --delete --force的快捷键
3. **-f**  --force：强制
4. **-m**  --move：移动或重命名
5. **-M**  --move --force的快捷键
6. **-r**  --remote：远程
7. **-a**  --all：所有



