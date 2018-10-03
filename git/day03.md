### git命令 ###
1. 仓库创建
	1. 初始化 git init
	2. 添加文件
		1. 将代码从工作区添加至缓冲区 
		2. 添加指定文件 git add <file> 
		3. 添加当前目录下的全部文件 git add .
	3. 代码提交
		1. 将代码从缓冲区添加至仓库区 
		2. git commit，通过vim书写版本信息
		3. 或git commit -m "版本信息" 
	4. 状态查询
		1. git status
	5. 查看版本记录
		1. git log
		2. git log --graph
		3. 版本记录是采用唯一的md5值。
	6. 首次提交需要配置
		1. git config --global user.email "your email"
		2. git config --global user.name "your name"
	7. 查看所有操作记录
		1. git reflog
	8. 代码下载
		1. git clone <https:xxx>
	9. 更新当前分支的新代码
		1. git pull
2. 代码回滚（本地仓库区）
	1. 回到上一个版本
		1. git reset --hard HEAD^	
		2. 注：几个^，向前回滚几次
	2. 回到指定版本
		1. git reset --hard <md5值的前6或7位> 
		2. 注：可前可后		
3. 撤销修改
	1. 把代码从缓冲区撤回工作区
		1. git reset HEAD  <file>
	2. 把工作区的修改丢弃
		1. git checkout -- <file>
4. 删除操作
	1. 从缓冲区删除提交，文件保存，即文件回到工作区
		1. git rm <file> --cached
	2. 从缓冲区删除提交，文件删除
		1. git rm <file> -f
5. 提交远程仓库
	1. HTTPS
		1. 方式一
			1. git add origin <https:xxx>
			2. git push origin <master>
			3. 优点：配置内容存在文件，后面提交默认提交到该仓库。
			4. 缺点：仓库切换不灵活。
		2. 方式二
			1. git push <https:xxx> <master>
			2. 优点：仓库切换自由。
			3. 缺点：每次提交都需要指明仓库，仓库信息未配置到文件中。
	2. SSH
		1. 无密码提交，配置方法
			1. ssh-keygen.exe生成公私钥，将公钥配置到GitHub的SSH keys（头像-》设置）中。
		2. 该方式提交时，将https部分替换成ssh方式的仓库地址，即可。
6. 分支管理
	1. 查询所在分支
		1. git branch
	2. 创建并切换到新分支
		1. git checkout -b dev
	3. 切换分支
		1. git checkout master
	4. 代码合并
		1. git merge dev
	5. 分支管理流程
		1. git checkout -b dev
		2. 修改代码
		3. git checkout master 切换回master
		4. git pull 拉取master最新代码
		5. git merge dev 从master分支上，合并dev分支
	6. 分支命令方式
		1. 人名
			1. 传统方式，一人负责一块
			2. 缺点：人员流动后，前任开发的代码，可能无人能懂
			3. 优点：长时间从事负责内容，可以精益求精
		2. 敏捷开发
			1. feature-100
			2. hotfix-99
7. 多人协作
	1. 在合作仓库下，项目-》设置-》Deploy keys-》Add depoy key，即给其他人员赋予权限
8. 忽略特殊文件
	1. 在根目录下 vim .gitignore
	2. 配置内容，可参阅：https://github.com/github/gitignore
	3. 过滤文件配置之后生效，之前的文件，不在管理范围之内
9. 工作常态（紧急处理bug）
	1. 正从事开发新项目，出现紧急bug。需要修改bug，马上完成上线，但新功能未完成，暂时不能上线。
	2. 处理方法
		1. 保存当前工作区代码
			1. 保存当前工作区
				1. git stash
			2. 查看保存清单
				1. git stash list
		2. 恢复工作区代码（之前开发的新代码）
			1. 恢复最近保存的工作区
				1. git stash apply
			2. 恢复指定的工作区备份
				1. git stash apply stash@{0}
		3. 删除保存区内容
			1. 删除上一个保存的工作区
				1. git stash drop 
			2. 恢复并删除上一个保存的工作区
				1. git stash pop 
9. 参与开源项目
	1. Django源代码
		1. 网址：https://github.com/django/django
	2. 流程
		1. 下载开源代码 git clone
		2. 修改代码
		3. 点击仓库的pull requests--》New pull request 
		4. 未完，待续

