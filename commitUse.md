# git commit

1. -a 参数设置修改文件后不需要执行 git add 命令，直接来提交。修改和删除过的，新文件无效。
--all
    Tell the command to automatically stage files that have been modified and deleted, but new files you have not told Git about are not affected.
    first looks at your working tree, notices that you have modified hello.c and removed goodbye.c, and performs necessary git add and git rm for you.

2. git commit TestRestore.txt -m '单独提交一个文件'
After staging changes to many files, you can alter the order the changes are recorded in, by giving pathnames to git commit. When pathnames are given, the command makes a commit that only records the changes made to the named paths:

3. 已经add等tracked过的文件，再修改了，可以直接commit，不用显式的add。

4. 未tracked过的文件的，直接commit的话 error: pathspec 'GitHubUse.txt' did not match any file(s) known to git

5. --amend
Replace the tip of the current branch by creating a new commit. 

6. 合并出现冲突，修正后再add，和commit完成最终的合并
