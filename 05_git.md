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
- 'git log' shows in reverse chronological order the list of commits
