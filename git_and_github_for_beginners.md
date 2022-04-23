# Git and Github for beginners Tutorial Notes

### GIT Installation
[Git Installation](https://www.atlassian.com/git/tutorials/install-git)

### Visual Studio code Installation
[VSCode Installation](https://code.visualstudio.com)

The recommended code editor is the 'Visual Studio code' editor.

### GIT course notes

[]()


### What is GIT ?
Free and open source version control system.

### What is version control ?
The management of changes to documents, computer programs, large websites and other collections of information.

### Important Terminology
- Directory -> Folder
- Terminal or command line -> Inteface for Text commands
- CLI -> Command Line Interface
- cd -> Change Directory
- Code Editor -> Word processor for writing code (E.g. Visual Studio code)
- Respository -> Project/folder where the project is kept.
- Github -> A website to host the repositories online. 

### Git Commands
- clone -> Bring a repository that is hosted somewhere like Github into a folder on your local machine
- add -> Track your files and changes in Git.
- commit -> Save your files in Git.
- push -> Upload Git commits toa  remote repo, like Github.
- pull -> Download the changes from remote repo to your local machine (the opposite of push).
- status -> check to see which files are being tracked or need to be commited.
- init -> use this command inside of your project to turn it into a Git repository and start using Git with that codebase.

### Managing Github Profile
- Create a Repository.
- Create a README.md (markdown) file.
- Copy the SSH key.

checking the git version.
```sql
git --version
```
cloning the repo to the local machine.
```sql
git clone <SSH Key>
```
Knowing the status of the files added/modified/deleted in the repository.
```sql
git status
```
Tracking 'all' of the untracked files in the repository.
```sql
git add .
```
Commiting the files to the repositiory
```sql
git commit -m "Custom_Message" -m "Custom_Description"
```
Sending the files from the local computer to online repository
```sql
git push
```
#### Connecting local machine to Github using SSH keys
ssh key has to be generated in the local machine. Here '-t' stands for type of encryption, '-b' denotes the strength of the encryption. The "email@github.com" is the github email id and it has to match with the registered email id of the github account.
```sql
ssh-keygen -t rsa -b 4096 -C "email@github.com"
```
The default location of the generated key is /Users/user/.ssh/id_rsa

There will be two keys generated 'key' and 'key.pub'. Here 'key' is the private key that should be kept secured at all times and 'key.pub' is the public key that should be shared.

```sql
cat /pathtofile/key.pub
```
Copy the key.pub.
- Go to the Github website. Go to 'Setings/SSH and GPG keys page.
- New SSH key. Give title and paste the public key.
- Add the SSH key to the ssh-agent [github page](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

### Git push
```sql
git push origin master
```
'origin' specifies the location of the git repository and 'master' the branch that we want to push out our information.

### Creating a Git repository in the local machine
- Create a folder. In this case demo-repo2
- move into the folder cd /path_to_folder/demo-repo2
- create/add the required files and folders in the folder demo-repo2
- To convert 'demo-repo2' into a git repository. Type
```sql
git init
```
- This can be followed by 'git status', 'git add', 'git commit' and 'git push' to make the folder 'demo-repo2' online.
Since we have created our respository locally there is a finite possibility that the git push couldn't find 'origin'. In that case we have to establish that connection.

#### Connecting to the origin (Destination repository)
- Create an empty git repository in the Github webpage with the same name. Here it is 'demo-repo2'
- Then there will be a page that say Quick setup. Copy the 'SSH address' in 'Setup in Desktop'.
- In the local machine. Type
```sql
git remote add origin <SSH address>
```
Check the connection
```sql
git remote -v
```
Now the connection is established to performt the push
```sql
git push -u origin master
```
Here '-u' is called the upstream or setting up a default connection to the origin. In the later cases it is sufficient to type 'git push' the changes will be realised in the origin. 

### Git Branching
Lets say if there is only one branch 'master'. All the changes/commits will reflect in this branch alone sequencially (commit 1,2,3,......). Now, let's say there is another branch 'feature' and the code is saved after commit 3 in the 'master' branch. The new commits done in 'feature' branch cannot be traced from master branch until the code is 'merged' with the master branch.
- To fix bugs we can create a 'hot fix' branch.

git branch will provide us the number of branches and on which branch the user is currently on (denoted with a * mark. Press 'q' to exit)
```sql
git branch
```
creating a new branch and switch to that new branch
```sql
git checkout -b <new_branch_name>
```
Switch to the concerned branch (always use 'git branch' to check after switching to the new branch)
```sql
git checkout <branch_name>
```
Before merging one would like to view the changes made in the code in the other branch w.r.t the master branch. (make sure you switch to master branch before using git diff)
```sql
git diff <branch_name>
```
merging the branch with the master (make sure you switch to master branch before using git diff).
```sql
git merge <branch_name>
```
Before merging the branch, make sure to push the changes made in that concerned branch.

To get the changes to the local machine
```sql
git pull origin master
```
To delete the branch (make sure you are not on that branch while deleting).
```sql
git branch -d <branch_name>
```
- Merge conflict - A single file modified by multiple users on different branches at the same time and trying to merge with the master. Then the git is incapable of deciding redundant information, this is called merge conflict.

For a modified file, to add and commit the recent changes we have
```sql
git commit -am "message"
```
### Undoing in GIT
If we have added changes/commited changes that we want to undo.

- undo staging (undo the 'add', before commiting it)
```sql
git reset <file_name>
```
or
```sql
git reset
```
- undoing commit
```sql
git reset HEAD~1
```
Here 'HEAD' means the pointer to the last commit and '1' denotes the number of commits/steps to go back further from the last commit(HEAD). 

To have a look of at all the commits(from latest to oldest)
```sql
git log
```
To unstage changes of a particular commit, First perform 'git log' copy the code of the particular commit 
```sql
git reset <commit_code>
```
This will unstage all the commits done after this particular commit.

Also, 
```sql
git reset --hard <commit_code>
```
here '--hard' denotes unstage and remove.So, it not only unstages the changes but also removes those lines from the concerned files.

### Forking
Forking is used to copy and get access/permissions to make changes in other users repositories.

### Further reading
- staching
- Forking
