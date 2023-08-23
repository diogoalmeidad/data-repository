## Typical Commands:
- Pull latest changes: $ git pull
- Create a directory: $ mkdir my-project
- Change into the directory: $ cd my-project
- Initialize a repository (project): $ git init .
- Stage the changes: $ add .
- Commit the changes: $ git commit -m "My changes"
- See log: $ git log

Concepts:
- Repository: Copy of a git project. Can be local (on the computer) or remote (hosting service)
- Commit: A version of the project
- Directory: A folder
- By default, the command prompt opens on the home folder which is represented by '~'
- Options: Settings that change the behavior of a command. It follows a '-' or '--'
- Arguments: Values that provide information to the command '<>' - they need to be replaced by user-supplied values
- Areas of Git:
   - Working Directory: Where all the modifications of the content of the project occur;
   - Staging: Where you prepare what you want to include in the next saved versions. The file is called 'index';
   - Commit history: Every time you make a commit it is saved in the commit history - a commit is a version of a project. Each commit has an ID (commit hash);
   - Local repository: Repository stored on a computer
 - Branch: A line of development. Normally there's a primary line of development (main) and secondary branches (feature branches) to work on a specific part of a project. These are incorporated or combined through merges and rebasing.
 - Merging: Process of integrating the changes made in one branch into another. You merge the source branch (contains changes) into the target branch (branch that receives changes, the one that is altered);
 - Merge Commit: Created to tie two development histories together when they diverge - has more than one parent;
 - Shortname: A local repository can communicate with a remote repository when the LR has a connection to the RR. The connection has a name - shortname. Usually origin;
 - When you push a local branch to a remote repository, a remote branch is created, which has a remote-tracking branch which is a reference in a local repository to the commit a remote branch pointed at the last time - like a bookmark;
 - To fully delete a branch you need to delete the remote branch, remote-tracking branch and local branch


Commands:
- 'pwd': Shows path to the current directory (print working directory)
- 'ls': List visible files and directories
- 'cd <path>: Change directory to a place. If I use 'cd ..' it goes back.
- 'mkdir <name>': Creates a directory (make directory)
- 'git config --global --list': Lists the variables in the Git configuration file and their values
- 'git init -b <name>': Initializes git with a branch with a specific name
- 'git status': shows state of the working directory and staging area -> shows which are the files that have been changed, but haven't yet gone to staging;
- 'git add -A': adds all files to the staging area and creates the 'index' file;
- 'git commit -m <message>': Makes a commit with a message;
- 'git log' shows in reverse chronological order the list of commits;
- 'git cat-file -p <commit hash>': Check which commit is the parent of which commit
- 'git branch': Gives list of branches;
- 'git branch <name>': Creates a new branch;
- 'git switch <name>' 'git checkout <name>': Switches to that branch;
- 'git merge <branch_name>': Integrates changes made from one branch into another branch;
- 'git checkout <commit_hash>': Checks out a commit, changing the head pointer to the commit you are changing into;
- 'git push': Upload data to a remote repository;
- 'git remote add <shortname> <URL>': Add a connection to a remote repository named <shortname> at <URL> (creates the connection);
- 'git remote -v': Lists the remote repository connections in the local repository with shortnames and URLs;
- 'git push <shortname> <branch_name>': Uploads content from <branch_name> to <shortname> remote repository (git push origin main);
- 'git branch --all': Lists all local and remote-tracking branches;
- 'git clone <URL> <directory_name>': Clone a remote repository (directory_name gives the name, or else it will keep the same name as in local - git clone https://github.com/diogoalmeidad/rainbow-remote.git friend-rainbow);
- 'git push <shortname> -d <branch_name>': delete a remote branch and the associated remote-tracking branch
- 'git branch -d <branch_name>': delete locally the branch 



