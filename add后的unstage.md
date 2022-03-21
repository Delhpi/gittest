# git add后的撤销restore--unstage：
    在于--staged参数，加参【就是放弃add】，操作的目标是暂存区，就是要让文件从暂存区消失，回到工作区，修改保留。
    不加【就是放弃修改】，操作的目标是工作区，里面的文件恢复成与暂存区里一致，如有add后的修改，会撤销；暂存区文件不变。 
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)

1. add后git restore --staged <file> 都会取消暂存区里的文件，文件回到工作区
    1.1 没有再修改，文件从暂存区移动到工作区，即文件不被追踪
    1.2 被修改了，文件从暂存区移动到工作区，即文件不被追踪；保留add后的修改

2. add后git restore  <file> 不使用--staged参数--文件还在暂存区，
    2.1 没有再修改。工作区文件本来就没有了，没有变化。
    2.2 被修改了。工作区文件没有了，（修改也被撤销了）

3. git rm --cached <file> 命令时，
    3.1 没有修改。从暂存区删除文件，工作区增加文件（Untracked ）。
    3.2 修改了。报错。参数中已staged的文件和工作区及HEAD中的内容都不同。
        error: the following file has staged content different from both the
        file and the HEAD:
        FileTestRestore.txt
        (use -f to force removal) 
        git rm --cached -f FileTestRestore.txt，暂存区文件没有了，工作区中还有，保留修改=1.2。

4. 网上说直接$rm，不行的。直接把文件删除了。相当于操作系统的删除命令了。

5. git reset HEAD file，文件回到工作区，若有修改也会被撤销。

6. git checkout -- <file>把文件从暂存区域复制到工作目录，用来丢弃本地修改。暂存区文件还有，2个区都有文件。前面1-3步骤，文件同时只在一个区里。