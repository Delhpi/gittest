#git add后的restore--unstage：
    在于--staged参数，加这个参数，操作的目标是暂存区，就是要让文件从暂存区消失；工作区文件不变。
    不加，操作的目标是工作区，里面的文件恢复成与暂存区里一致，如有add后的修改，会撤销；暂存区文件不变。  
1、add后git restore --staged <file> 都会取消暂存区里的文件
    1.1没有再修改，文件从暂存区移动到工作区，即文件不被追踪
    1.2被修改了，文件从暂存区移动到工作区，即文件不被追踪；保留add后的修改

2、add后git restore  <file> 不使用--staged参数--文件还在暂存区
    2.1没有再修改。工作区文件本来就没有了，没有变化。
    2.2被修改了。工作区文件没有了（好像修改也被撤销了。等于把工作区的修改给Restore了）

3、git rm --cached <file> 命令时，
    3.1没有修改。从暂存区删除文件，工作区增加文件（Untracked ）。
    3.2修改了。报错。参数中已staged的文件和工作区及HEAD中的内容都不同。
        error: the following file has staged content different from both the
        file and the HEAD:
        FileTestRestore.txt
        (use -f to force removal) 
        git rm --cached -f FileTestRestore.txt，暂存区文件没有了，工作区中还有，保留修改=1.2。

4、 网上说直接$rm，不行的。直接把文件删除了。相当于操作系统的删除命令了。       
