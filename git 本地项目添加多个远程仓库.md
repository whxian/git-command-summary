# git 本地项目添加多个远程仓库

### 方式一

1. 添加一个远程库 名字不能是origin 

```javascript
git remote add <origin-alias> <SSH>
// eg:
// git remote add aliyun git@code.aliyun.com:***.git
```

2. 查看远程库及地址

```javascript
git remote -v
```

3. 拉，推

```javascript
git pull <origin-alias> 远程分支名：本地分支名
git push <origin-alias> 本地分支名：远程分支名
// eg:
// git pull aliyun aliyun_master: aliyun_master_dev
// git push aliyun aliyun_master_dev: aliyun_master
```

### 方式二

1. 添加另外一个远程库

```javascript
git remote set-url --add origin git@code.aliyun.com:***.git
// 相当于以下两个命令
// git remote add origin git@code.aliyun.com:***.git
// git remote set-url origin git@code.aliyun.com:***.git
```

2. 查看远程库及地址

```javascript
git remote -v
```

3. 推**（推送时，可以同时推送到另外一个库）**

```javascript
git push origin 本地分支名：远程分支名
```

### 取消本地目录下关联的远程库

```javascript
git remote remove <origin-alias>
// eg:
// git remote remove aliyun
// git remote remove origin
```

