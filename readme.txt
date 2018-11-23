
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
git reflog --查看历史命令

git reset --hard head^ --恢复上一个版本
git reset --hard commit_id --按版本号恢复版本
git reset head file --从暂存区恢复到工作区

git checkout -- file --文件保存了，恢复到没保存之前的状态

rm file --删除工作区文件
git rm file --删除版本库文件到暂存区，记住删除后要提交

ssh-keygen -t rsa -C "youremail@example.com" --生成一个SSH keygen
git remote add origin git@github.com:yourName/yourRepository.git --关联远程库

git push -u origin master --向远程库推送最新版本，如果远程库有内容则不需要-u参数省略
git clone git@github.com:yourName/yourRepository.git --从远程库克隆最新版本到本地工作区

git branch --查看分支
git branch branchname --创建分支
git checkout branchname --切换分支
git checkout -b branchname  --创建并切换分支加-b参数
git merge branchname --把分支合并到master主分支上
git branch -d branchname --删除分支

create a new branch (quick and simple) or (quick & simple).





