
2017.1.11
# use git to update nonmaster branch
## sync latest code and create local branch to remote rb branch
git fetch
git branch -a
git checkout -b local_170111 remotes/origin/rb-xxx
## sync submodule dependence
git submodule init
git submodule sync
git submodule update --init --recursive
## sync latest code of remote rb branch
git fetch origin
## cherry pick from master branch
git cherry-pick md5_commit_id
git diff remotes/origin/rb-xxx
## if submodule changed, commit it
cd submodule_dir
git branch
git checkout master  # if not on master
git pull
cd ..
git diff
git add submodule_dir
git status -s
git commit -m"......"
git log  # check all main module and sub module have been commit
## push to remote
git push origin local_170111:rb-143

2017.1.5
apply patch
diff -u sa/query_server.ini ~/9-test/query_server.ini > ini.patch
vi ini.patch   # modify the query.ini path in init.patch
ll s? [tab tab]# get array: sa/ sc/ sd/ se/ sf/ sg/ sh/ si/ sx/
./do_patch.sh ini.patch sa/ sc/ sd/ se/ sf/ sg/ sh/ si/ sx/

2017.1.4
.gitignore
.git/info/exclude

2017.1.3
git blame, Show what revision and author last modified each line of a file
git blame filename
git blame <commit>^ -- filename | head -3 | tail -2

ads common, rerieval have not rb branch
only ads_server have rb branch

git fetch
git branch -a		#显示all 分支列表
git checkout -b local_170103 remotes/origin/adserver-rb-143

Ad Server
git submodule init	# sync submodule
git submodule sync
git submodule update --init --recursive
git fetch origin  	#远程分支更新拉回本地
git cherry-pick md5_commit_id
git diff remotes/origin/adserver-rb-143
git push origin local-rb-143:adserver-rb-143

ads_common
git add ads_common
git diff ads_common
git add ads_common
git commit -m"submodule cherry-pick md5_commit_id"
git push origin local-rb-143:adserver-rb-143

2016.12.19
update submodule
cd adserver/sh
sh crtool.sh up_sub

2016.12.12
1. sync code
git clone git@git.jd.com:ads-serving/adserver.git
git submodule update --init --recursive

2. git pull
git pull <远程主机名> <远程分支名>:<本地分支名>
git pull origin next:master
git pull origin next   ( == git fetch origin; git merge origin/next)
