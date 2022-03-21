Title: git hooks post-receive 中 git pull 失败
Date: 2017-12-11 15:35:51
Category: git
Tags: git
Slug: git-hooks-post-receive

git 在运行时会用 $GIT_DIR 这个环境变量

解决方法是在hooks脚本里面加上 `unset $(git rev-parse --local-env-vars)`

或者使用 env -i git pull
