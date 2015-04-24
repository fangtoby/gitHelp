配置用户信息

	git config --global user.name "Your Name Comes Here"
	git config --global user.email you@yourdomain.example.com 

配置别名

	命令行修改配置文件
	git config --global alias.st status //git status == git st
	git config --global alias.co checkout
	git config --global alias.ci commit 
	git config --global alias.br branch
	
	修改配置文件
	 vi ~/.gitconfig
	[alias]
        st = status
        co = checkout
        ci = commit
		ca = commit -a
		l = log --stat
        br = branch
        ba = branch -a
        br = branch -r
        pl = pull
        pr = pull --rebase
        ps = push
		
初始化git
	
	git init

把文件添加到仓库

	git add filename
	
把文件提交到本地仓库

	git commit -m "comment message"

查看历史记录
	
	git log
	
指定远程仓库

	git remote add origin git@github.com:fangtoby/gitHelp.git

推送到远程仓库

	git push -u origin master

创建远程分支
	
	git push origin master:testGitPush

删除分支

	//删除本地
	git branch -d testGitPush
	//删除远程
	git push origin :testGitPush

推送到远程指定分支

	由root在gitlab上面给每个master建立一个branch-dev的分支，给
	大家提交开发。这个是有权限的。只是需要在push的时候要指定分支。
	提交代码到远程develop分支，然后由root来合并
	
	git push origin master:develop

还原修改文件

	git reset --hard HEAD^
	
	git reset --hard 3628164

还原已经提交的修改

	git revert HEAD    撤销前一次 commit
	git revert HEAD^   撤销前前一次 commit
	git revert commit-id （比如：fa042ce57ebbe5bb9c8db709f719cec2c58ee7ff）
	
丢弃工作区的修改

	git checkout -- filename

把暂存区的修改撤销掉（unstage），重新放回工作区

	git reset HEAD  filename
	
从版本库中删除该文件，那就用命令git rm删掉，并且commit

	git rm test.txt

	git commit -m "remove test.txt"

另一种情况是删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本

	git checkout -- test.txt
	
创建针对指定远程分支的本地分支进行开发

	git branch NewLocalBranchName origin/remoteBranch
	
使用rebase推送而非merge减少无用的merge消息，从而保持历史记录的清晰。

	git pull --rebase
