### git安装 ###
Git可以在Linux、Unix、Mac和Windows这几大平台上正常运行。

官网：https://git-scm.com/

Debian或Ubuntu Linux，通过一条sudo apt-get install git就可以直接完成Git的安装。

安装git完成，在目标目录下，右键，选择“Git Bash Here”，就进入了小型Linux系统，即git命令操作窗口。

### git三区 ###
1. 工作区（working Directory）
2. 缓冲区（舞台）（stage zone）
	- 作用
		- 提交缓冲区
		- 部分提交确认区
		- 提交确认区
3. 本地仓库区（版本库）（代码库）（repository）
	1. 提交上代码库，一切有记录，即使删除也不好使。
	2. 分支
		1. 仓库区的主分支为master，通常用于存放稳定版本代码，不能在上面开发的。
		2. dev 分支：测试版
		3. stage/pre-production:预上线（可有可无，看需求）
4. 远程仓库区（GitHub）
	1. 提交方式
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
	2. 配置文件
		1. vim .git/config


工作区---> 缓冲区，实现方式：git add

缓冲区---> 本地仓库区，实现方式: git commit

缓存区 ---> 工作区，实现方式： git reset HEAD <file>

丢弃工作区的修改， 实现方式： git checkout -- <file>

注：也可以配置自己的代码库（gitlab），不使用GitHub。但相比GitHub的一年六百元的开销，部署本地代码库的成本、稳定性、容灾能力都逊色很多。