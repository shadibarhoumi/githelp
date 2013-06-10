# local branch creation #

First, you must create your branch locally. Create a branch for every feature you work on.

	git checkout -b your_branch

# basic git workflow #

	git add .
	git commit -m "message"
	git status

# Initial push back up to github repo #

After that, you can work locally in your branch, when you are ready to share the branch, push it. The next command push the branch to the remote repository origin and tracks it. 
	git push -u origin your_branch

# teammates can play too! #

Teammates can reach your branch, by doing:
	
	git pull
	git checkout origin/your_branch

# push existing branches (after initial commit) #

You can continue working in the branch and pushing whenever you want without passing arguments to git push (argumentless git push will push the master to remote master, your_branch local to remote your_branch, etc...)

	git push

Teammates can push to your branch by doing commits and then push explicitly.

#When you want new code from another branch#

	git rebase

To pull down the latest changes from the a branch to you local feature branch, you must merge the branch with your local feature branch. 

	git checkout your_branch 
	git merge branch_with_desired_code

#Careful: don't merge master locally#

	BAD: git checkout master
<code><strike>BAD: git merge your_branch</strike></code>
<code><strike>BAD: git push</strike></code>

Basically we don't want stuff committed to the master branch from a local repo. We want to use pull requests through git hub to commit production code. 

#finalize to production code#

Push your branch up, then goto github and open a pull request between your code and the master branch. Then ask a backend guy to review the code and close the pull. 

reset the origin: 
	
	git remote set-url origin <url>


#A basic workflow#
	
	git push origin HEAD:refs/heads/your_branch

	git checkout --track -b your_branch origin/your_branch
... work ...
	git commit
... work ...
	git commit
	git push

#Configuring Git#

First you need to tell git your name, so that it can properly label the commits you make.

	git config --global user.name "Your Name Here"

Git saves your email address into the commits you make. The email address is used to associate your commits with your GitHub account.

	git config --global user.email "your_email@example.com"

The last option we need to set will tell git that you don't want to type your username and password every time you talk to a remote server. This will set git to use the credential memory cache.

	git config --global credential.helper cache

By default git will cache your password for 15 minutes. This can be change like so, with timeout setting in seconds.
	
	git config --global credential.helper 'cache --timeout=3600'
