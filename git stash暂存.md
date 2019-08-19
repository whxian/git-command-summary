## git stash

将目前还不想提交的但是已经修改的内容保存至堆栈中，后续可以在某个分支上恢复出堆栈中的内容，stash中的内容不仅仅可以恢复到原先开发的分支，也可以恢复到其他任意指定的分支上。 

1. `git status`

   将所有未提交的修改（工作区和暂存区）保存至堆栈中，用于后续恢复当前工作目录

   > `git stash save`
   >
   > 作用等同于git stash，区别是可以加一些注释
   >
   > ```javascript
   > // git stash save 'test1'的效果
   > stash@{0}: On master: test1
   > ```
   >
   
2. `git stash list`

   查看当前stash中的内容

3. `git stash pop`

   恢复同时把stash内容删除

   > `git stash apply`
   >
   > 恢复并且不删除stash内容，适用于多分支恢复
   
   > 指定恢复哪个stash到当前的工作目录：`git stash apply + stash名字（如stash@{1}）`

---

1. `git stash drop + 名称`

  从堆栈中移除某个指定的stash
  
2. `git stash clear`

   清除堆栈中的所有内容

3. `git stash show`

   查看堆栈中最新保存的stash和当前目录的差异

   > 查看指定的stash和当前目录的差异：`git stash show stash@{1}
   >
   > 查看详细不同：`git stash show -p`
   >
   > 查看指定的stash的差异内容：`git stash show stash@{1} -p`

4. `git stash branch`

   从最新的stash创建分支

   

   

   