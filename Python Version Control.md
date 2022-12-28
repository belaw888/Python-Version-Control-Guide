# Python Version Control

## Using git, github, pip, and virtualenv

Each of these components individually are quite commonly used. However, the way in which all of these are used together is specific to our use case.

* * *

### Overview of Definitions

- **Version Control** \- keep track of changes to files in a project over time: *what* they are, *who* made them, and *when* they were made
- **Git** \- open source version control software
- **GitHub** \- free to use online repository based on Git version control, frequently used to store backups and for remote collaboration
- **Package Manager** \- software almost always relies on other software. In Python, installing publicly available code (called packages) is a tool that saves time and energy. In other words: *don't reinvent the wheel!*
- **Pip** \- a package manager for the Python language
- **Dependency Manager** \- our project will be *dependent* on the packages we install. Installing these packages directly to our computer is fine at first, but if you have more than one project, their dependencies will conflict with each other. A dependency manager prevents these conflicts. More info on the mess that is dependencies [here](https://www.fullstackpython.com/application-dependencies.html)
- **Virtualenv** \- a dependency manager for the Python language. It works by creating a "virtual environment" with a special folder to store dependencies. That way, if each project has its own virtual environment, there is no worry about the dependencies of different projects impacting each other.

## Starting a Python project using Linux ([Debian Based Distros](https://www.debian.org/derivatives))

### 1\. Creating a virtual environment and installing packages:

*If you do not have **pip** installed, follow [these](https://www.geeksforgeeks.org/how-to-install-pip-in-linux/) instructions*

Start by creating a new folder (also called a *directory*) for your project. Use the command line to run `mkdir project_name` (where "project_name" is replaced with your project's name)

Run `cd project_name` to open the directory.

*If you do not already have **virtualenv** installed, follow the instructions in [this](https://www.geeksforgeeks.org/creating-python-virtual-environment-windows-linux/) article.*

Otherwise, run `virtualenv env` to create a virtual environment within this directory. Note that "env" is just the name of the virtual environment. It could be replaced by whatever you want, but "env" is just a common naming convention.

Run `ls` to verify a folder called "env" has been created in the current directory.

If so, run `source env/bin/activate` to activate the virtual environment. Your command line should now look something like:

`(env) username@operating-system:~/project_name$`

When you are finished working in the virtual environment, simply run `deactivate`.

**You are now ready to install packages!** To do so at any time, activate the virtual environment if you haven't already.

Now, run `pip install package_name`. For example, to download the data analysis library **pandas**, you would run `pip install pandas`.

*Remember that if you do not have **pip** installed, you need to do so. If this is the case, deactivate your virtual environment, return to your home directory, and follow the instructions at the beginning of this section.*

### 2\. Creating a local Git repository

Once you are done installing packages for now, `deactivate` your virtual environment.

*If you do not already have **Git** installed or you are unsure, return to your home directory and follow the instructions in [this](https://www.linode.com/docs/guides/how-to-install-git-on-linux-mac-and-windows/) article. Return to the project directory when you are finished*

Run `git init` to create a new Git repository in your current directory.

Now run `echo 'env' > .gitignore` to prevent Git from saving dependency files to the repository. To learn more about why this is important, read [this](https://realpython.com/python-git-github-intro/#gitignore) and [this](https://realpython.com/python-git-github-intro/#what-not-to-add-to-a-git-repo).

However, these dependencies are necessary for anyone trying to run your project. How can we record what packages we used while using .gitignore as described above? By using a **requirements.txt** file!

This file will contain all of the package names and their respective versions. To create it, run `pip freeze > requirements.txt`. 

### 3. Maintaining a repository using Git and GitHub
[This](https://www.youtube.com/watch?v=gJv0PcfUXE8) video is a must watch. 

To push your changes to the local repository to GitHub, run `git push origin main`, where "main" is the name of your branch.

To work on this project on a different computer, first clone the repository from GitHub as described in the video. Next, activate the virtual environment and run `pip install -r requirements.txt` to install all package dependencies. 

**Congratulations! Your project can now be run by anyone with acess to your GitHub!**

Read [this](https://www.git-tower.com/learn/git/faq/create-branch) to learn about git *branches*.

## Helpful Commands

| Command | Description |
| --- | --- |
| `cat .git/config` | Displays Git repo config info, including the remote repository url, if any. |
| `cat .gitignore` | Displays content of .gitignore file |
| `git log --oneline` | Outputs a list of all commits to the repository, one per line |
|`pip list`|description|
|`git status`|description|

## Sources
* https://towardsdatascience.com/python-environment-101-1d68bda3094d
* https://packaging.python.org/en/latest/tutorials/managing-dependencies/
* https://docs.python-guide.org/dev/virtualenvs/
* https://www.atlassian.com/git/tutorials/syncing/git-pull
* https://learnpython.com/blog/python-requirements-file/
* https://openclassrooms.com/en/courses/6900846-set-up-a-python-environment/6990328-name-your-virtual-environments
* https://medium.com/wealthy-bytes/the-easiest-way-to-use-a-python-virtual-environment-with-git-401e07c39cde
* https://realpython.com/python-virtual-environments-a-primer/
* https://hackr.io/blog/basic-linux-commands
* https://realpython.com/python-git-github-intro/
