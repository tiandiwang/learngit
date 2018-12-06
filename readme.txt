在开始菜单里找到“Git”->“Git Bash”启动Git命令行窗口

git config --global user.name "your name" --设置Git全局用户名
git config --global user.email "your email" --设置Git全局邮箱

mkdir working directory--创建工作区（文件夹）
cd working directory --进入工作区
pwd --查看工作区路径
git init --创建版本库（.git文件夹）

git add file --把文件加入到版本库的暂存区
git commit -m "file comment" --把暂存区的文件提交到版本库

git status --查看工作区当前情况
git diff --查看工作区文件修改了什么
git diff head -- file --查看文件工作区和版本库最新版本的区别

git log --查看版本库当前状态
git log --pretty=oneline --按行输出版本库当前状态
git log --graph --pretty=oneline --abbrev-commit --查看分支合并图
git reflog --查看历史命令

git reset --hard head^ --恢复上一个版本
git reset --hard commit_id --按版本号恢复版本
git reset head file --从暂存区恢复到工作区

git checkout -- file --文件保存了，恢复到没保存之前的状态

rm file --删除工作区文件
git rm file --删除版本库文件到暂存区，记住删除后要提交

ssh-keygen -t rsa -C "youremail@example.com" --生成一个SSH keygen
git remote add origin git@github.com:yourName/yourRepository.git --关联远程库

git push -u origin <branch_name> --向远程库推送最新版本，如果远程库有内容则不需要-u参数省略
git clone git@github.com:yourName/yourRepository.git --从远程库克隆最新版本到本地工作区

git branch --查看分支
git branch <branch_name> --创建分支
git checkout <branch_name> --切换分支
git checkout -b <branch_name>  --创建并切换分支加-b参数
git merge <branch_name> --把分支合并到master主分支上
git branch -d <branch_name> --删除分支

在实际开发中，我们应该按照几个基本原则进行分支管理：
1. master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；
2. 每个人都建立自己的分支，比如：bob、michal......，每个人在自己的分支上干活；
3. 建立dev分支，这个分支应该是每个人把自己的分支时不时地往dev分支上合并就可以了。
4. 合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

--bug branch 
git stash --暂存当前未提交的分支工作内容
git stash list --查看已暂存的分支
git stash pop --恢复暂存的分支继续工作

--feature branch
1. 开发一个新feature，最好新建一个分支；
2. 如果要丢弃一个没有被合并过的分支，可以通过git branch -D <branch_name>强行删除。

--remote origin
git remote -v --查看远程库的信息
git remote add origin git@github.com:yourName/learngit.git --关联远程库
git remote rm origin --删除关联远程库

推送分支，就是把该分支上的所有本地提交推送到远程库。推送时要指定本地分支，这样Git就会把该分支推送到远程库对应的远程分支上：
git push origin <branch_name> --向远程服务器推送分支
   
并不是一定要把本地分支往远程推送，那么，哪些分支需要推送，哪些不需要呢？
1. master分支是主分支，因此要时刻与远程同步；
2. dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；
3. bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；
4. feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。
总之，就是在Git中，分支完全可以在本地自己藏着玩，是否推送，视你的心情而定！多人协作时，大家都会往master和dev分支上推送各自的修改。

抓取分支，从远程库抓取所有分支到本地库，clone时默认情况下只能看到本地的master分支。
git clone git@github.com:yourName/yourRepository.git --从远程服务器抓取master分支，而你要在dev分支上开发，就必须创建远程origin的dev分支到本地：
git checkout -b <branch-name> origin/<branch-name>

因此，多人协作的工作模式通常是这样：
1. 可以试图用git push origin <branch-name>推送自己的修改；
2. 如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
3. 如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。
4. 再进行git pull 如果合并有冲突，则解决冲突，并在本地提交；
5. 没有冲突或者解决掉冲突后，再用git push origin <branch_name>推送就能成功！
这就是多人协作的工作模式，一旦熟悉了，就非常简单。

--tag
git tag <tag_name>  --为当前提交创建版本号
git tag <tag_name> commit_id --根据以前提交的ID号创建版本号
git tag --查看所有版本号
git show <tag_name> --查看版本号文件的具体内容

git push origin <tagname> --把版本号推送到远程库
git push origin --tags --把所有版本号推送到远程库

git tab -d <tag_name> --删除本地版本号
git push origin :refs/tags/<tagname> --删除远程库中的一个版本号






