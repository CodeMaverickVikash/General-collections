Git working
first is working directory --- second is staging area --- git directory/repository

git remote -v // to check which origin is added

Configuration for git bash only once
git config --global user.name your_name
git config --global user.email your_email
git config --global user.password your_password

checking
git config --global user.name
git config --global user.email
############################################################

git init // This Command initialize folder as empty git repo
STAGGING - git add . // This Command add all files present in current directory

git restore --staged <file_name> // to unstage

COMMIT - git commit -m "initial commit" // This command will commit/save all changes
check status command is git status // everything okay

git remote add origin link_here_of_your_repo_SSH_wala // You have to add remote origin means yesi website or server which will save our code 
git push origin master or git push origin master --force // It will push/upload your code on website

// To update remote
git remote set-url origin new_url


git pull origin master // For pulling code
git log // If you want to see kisne kya changes kiya your repo me use this cmd

git branch // To see what branch you are using

git show ssh_key // Review your changes

git diff file_name // Review your changes
git diff --staged file_name // To see staged file changes


 Branches (Create, Merge, Delete a branch) 

1) git branch // to show branches
2) git branch BRANCH_NAME // it will create new branch
3) git checkout BRANCH_NAME // to active ealier created branch

Merce two branches
first you need to go main branch, then run commant "git merge BRANCH_NAME" 

git checkout -b BRANCH_NAME // create branch and checkout above both command in single line, it will create branch from where you are currently

Go to main branch, then run command "git branch -d BRANCH_NAME" // in order to delete dummy branch


push new branch to github
First need to checkout what branch you want to push, then run command "git push --set-upstream origin BRANCH_NAME"



explore command - git reset <commit_hash> && git stash && git stash pop 


Working on existing project --------->
Que. Why Fork and How to fork?
If you don't have permission to change anything in existing project and you want to contribute something, then you need to fork it, 
Fork means copy of the project in your own account so that you can change and contribute.

git remote -v // To show attach origin

// What is upstream and adding it to local
git remote add upstream "URL_FORM _YOU FORKED"

origin - your own account
upstream - not your own account

// To remove commit
git log
git reset "Copy_bellow_commit_hash_to_remove_upper_commit"
git status
?? show up: unstaged
git add .
git stash
git log 
?? everything will be good

Merge conflicts and how to resolve them?

Fix the last pushed commit author and email
git commit --amend --author="Your Name <your@email.com>"
git push --force
⚠️ Force push is safe only if you’re the sole contributor on that branch.


Git Tutorial 5: Undoing/Reverting/Resetting code changes

1) Undo uncommited changes -------------> "git checkout -- ."
2) Undo commited changes -------------->  "git revert <commit_id>" or "git revert -n <commit_id>" for no commit - it will take into unix editor, to exit just write ":q" and enter
3) Resetting changes ------------>   "git reset --hard <select commit id on which state do you want to go>" // previous state

// git log --------> show only history of your code how it was envolved
// git log --oneline --graph --decorate ----> show history of commit in graph form

git log flow

   latest commit (upper)
	|
	|
	|
	|
   old commit (lower)


Head is a reference to the most recent commit in current branch (in most of the cases) ------> HEAD and latest commit both are same or we can say HEAD is the short form of most recent commit
git show HEAD
git show <latest commit>

Detached Head senario - when HEAD doesn't point to most recent commit, you go into detached HEAD state.


GIT CHERRY-PICK
1) Bring changes from specific commit
2) Choose one or more commits
git cherry-pick <commit id>  ---------------> it will make commit automatically
git cherry-pick <commit id> -n  ---------------> it will stage but not make commit // it will not work with merged commit


in vscode
# stash technique used during switching branch
stash - branch no matter, do this when you don't want to commit your code but you want to keep that,
it save in your system. before it need to staged.
apply latest stash - come all changes after done stash.

git pull origin BRANCH_NAME // take pull from remote repo

ERROR:
hint: Please, commit your changes before merging.
Solution: 'git commit -m "Case_Ticket_No"'
EX: 'git commit -m "BLDBTRPFST-539"'

"git fetch": refresh the repository

how to know which function is bind to element??

// Lookup events for this particular Element
$._data( $('css_selector')[0], "events" );

Error: There is no tracking information for the current branch.
Solved: git branch --set-upstream-to=origin/master master


git merge --abort // solve the merging problem

Unwanted changes are not gone after discarding changes with git, to resolve this issue, need to run the below command:
git rm --cached -r .
git reset --hard

Don't do undo last commit because it create some extra commit in bitbucket which is not good.


Applying the changes from branch A to B, without merging or adding commits (Similar to pull request merge):
git merge --no-commit --squash branchA
git reset HEAD # to unstage the changes

Note: for merge: sync both branch remotely, checkout banch B and do above things

How to Check WHICH REPO You Are In (Most Important) and where code fetch and push?
git remote -v
origin  git@github.com:account1/my-repo.git (fetch)
origin  git@github.com:account1/my-repo.git (push)

✅ This means:
Push will go to account1
Repo = my-repo
📌 GitHub account is decided by remote URL, NOT by user.name.

How to Check Commit Author for THIS Repo?
git config user.name
git config user.email



how to manage multiple github accounts from one PC? want clone repo from different github account so need to login accordingly.
1. create .ssh folder in root and go inside using "mkdir ~/.ssh && cd ~/.ssh"
2. Generate key for each account using "ssh-keygen -t ed25519 -C "personal-email@example.com""
3. create .bash_profile file in root (~) and add below code
# Auto-start ssh-agent
env=~/.ssh/agent.env

agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }

agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }

agent_load_env

agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add ~/.ssh/your_first_personal_account_file_name
    ssh-add ~/.ssh/your_second_work_account_file_name
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add ~/.ssh/your_first_personal_account_file_name
    ssh-add ~/.ssh/your_second_work_account_file_name
fi

unset env

and run below command
# Reload the profile
source ~/.bash_profile

verify ssh-add -l

Add Public Keys to GitHub / GitLab
copy from cat ~/.ssh/file_name_personal.pub

Paste into:
GitHub → Settings → SSH & GPG keys → New SSH key

Repeat same step for others

Next (IMPORTANT): Configure SSH for Multiple Accounts
Create config file:

nano ~/.ssh/config

# Personal GitHub
Host github-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_personal

# Work GitHub
Host github-work
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_work


Set permission:
chmod 600 ~/.ssh/config

✅ Test Connections
ssh -T git@github-personal
ssh -T git@github-work

Uses:
git clone git@github-work:work-username/repo.git
git clone git@github-personal:personal-username/repo.git

ssh-add -l

done success
git clone git@github-work:TruenoTech-in/Track-Shipment.git

// Test personal
ssh -T git@github-purpose92
ssh -T git@github-vmaskhare
ssh -T git@github-gagan


npm i -g @railway/cli -> run all command in project root dir
railway whoami - who logged in
railway login
railway init -> select workspace and create project
railway link -> select workspace and link existing project
railway up -> to deploy
