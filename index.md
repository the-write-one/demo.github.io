# Forking GitHub Repositories and Creating Pull Requests

Learn to use the GitHub web application and Git command-line tools to clone a Git repository, make changes and create a pull request for merging your changes into the source project.

**Contents**
- [Prerequisites](#prerequisites)
- [Logging into GitHub](#logging-into-github)
- [Finding and Forking the Test Repository](#finding-and-forking-the-test-repository)
- [Cloning the Fork Using Git Command Line](#cloning-the-fork-using-git-command-line)
  - [Installing Git](Installing_Git.md)
  - [Setting Up SSH Key](SSH_Key.md)
- [Creating a Pull Request](#creating-a-pull-request)
- [Additional Resources](#additional-resources)

## Prerequisites

The following software and tools are used:

1. Chrome browser (version 85.0.4183.121).
You can use a browser of your choice to download Git.
  
2. Windows 10™ operating system.

## Logging into GitHub

GitHub is a web application and online repository based on the Git version control system.
The GitHub web application allows browsing existing repositories, and performing certain maintenence tasks
in the browser, such as creating a new repository, cloning existing repositories, making simple file changes, 
committing the changes, merging into the source (or upstream) project using pull requests, etc. 

To log into GitHub:
1. Open the link [https://github.com/](https://github.com/) in your web browser. If you are already signed in, proceed to the next section.
2. To sign in, if you already have an account, choose **Sign In** from the top-left menu.
3. Enter your user name and password, click **Sign In**.

<img src="clone/01_Log_In.png" width="400">

> 💡 If you don't have a GitHub account, select **Sign Up** or follow the link [https://github.com/join](https://github.com/join).
> Enter **Username**, **Email** and **Password**, and select **Create Account**. Follow the directions to verify your email address.<br>
> <img src="clone/02_Join.png" width="400">

## Finding and Forking the Test Repository

Once logged in, you should see the GitHub web page with your account icon on the right.

1. Locate the **Search or jump to...** field.

<img src="clone/03_Search.png" width="500">

2. Enter `nobl9/writingtest` in the search field and press Enter. You should see the repository in the search result.

<img src="clone/04_Find.png" width="500">

3. Click the repository name `nobl9/writingtest` in the search results to navigate to the repository page.

<img src="clone/05_Repo_Page.png" width="500">

4. On the repository page, click the **Fork** button on the top left. Wait for the forking process to complete.

<img src="clone/06_Forking.png" width="500">

5. Once forking is complete, you should see the `writingtest` repository under your account.

<img src="clone/07_Forked.png" width="500">

Next, we will clone the forked repository on a local maching using Git command line.

## Cloning the Fork Using Git Command Line

Cloning a Git repository creates a local copy on your computer for working remotely. Git command line tools allow syncing changes between the two locations. 

The separate tutorials below provide details how to install and configure them on your local computer.

- [Installing Git](Installing_Git.md) <br> This tutorial is intended for novice Git users and guides you through the step-by-step Git Setup Wizard. You will need to install Git to use the command line tool.

- [Setting Up SSH Key](SSH_Key.md) <br> Procedures to generate, set up an SSH key and use it with a GitHub account. <br> With SSH keys, you can connect to GitHub without supplying your username or password at each visit. <br> SSH is an optional alternative to an HTTPS connection, which does not have a key configuration step, but will require username and password for Git operations.

### Cloning the Repository Locally

1. Navigate to your fork of the repository in GitHub. Click the **Code** button above the file list.

<img src="clone/20_Clone_HTPPS.png" width="600">

2. Select either **HTTPS** or **SSH** (optional) tab depending on type of connection used for Git.<br>
   Click the highlighted **Copy** icon to place the URL in the clipboard.
   
3. Open **Git Bash** from the Windows Start menu.

4. Change the current directory to the parent folder, where the cloned repository will be placed. Here we will create a new directory and change into it.
```
$ mkdir github
$ cd github
```

5. Type `git clone ` (ending with a space), then paste the URL (Right-Click), and press Enter. <br>
   The URL will depend on whether **HTTPS** or **SSH** was chosen earlier, but the process is the same.
```
$ git clone https://github.com/the-write-one/writingtest.git
Cloning into `writingtest` ...
```
In case of SSH, the URL will look like this:
```
git clone git@github.com:the-write-one/writingtest.git
```

### Making Local Changes

1. Locate the `README.md` file in the repository folder
2. Open the file in a text editor. **Notepad** or **Notepad++** can be used.
3. Make some changes in the text file.
4. Save the changes in the same file. Exit the text editor.

It is a good idea to verify that the changes are made in the correct file and are ready to be committed:
```
$ git status
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
        modified:   README.md
```
> 💡 Note: `origin/master` are the names of the repository and the branch, which are later used in [Pushing to the GitHub Server](#pushing-to-the-github-server).

### Committing the Change Locally

Git **commit** captures a series of changes in a local repository. A separate **push** step is used to send the changes to the GitHub server.

1. Locate the repository folder in the command line (Git Bash). Use `cd writingtest` if needed.
2. Type `git commit -a -m "<message>"`, where `<message>` is the commit comment
```
$ git commit -a -m "Other change"
1 file changed, 2 insertions(+)
```

> 💡 Using **HTTPS** may require configuring the username and email. Such as running:
> ```
> git config --global user.email "you@example.com"
> git config --global user.name "Your Name"

### Pushing to the GitHub Server

1. Type `git push` and press Enter <br>

> 💡 Note: Optional omitted parameters `<repository> <branch>` are `origin` and `master`, typical for working with the default main branch.
> To verify the repository name and URL use `git remote -v`.
> ```
> $ git remote -v
> origin  https://github.com/the-write-one/writingtest.git (fetch)
> origin  https://github.com/the-write-one/writingtest.git (push)
> ```
> The name of the active branch is shown using `github status` (see [Making local changes](#making-local-changes) above).

2. (Only if **HTTPS** is used) enter **Username** and **Password** at the prompt.
```
$ git push

Username for 'https://github.com': the-write-one
Password for 'https://the-write-one@github.com':
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 304 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/the-write-one/writingtest.git
   53ff74c..98d0755  master -> master
```

At this point, you may want to verify the changes at the GitHub server:

<img src="clone/21_Server_Changes.png" width="600">

## Creating a Pull Request

*Pull request* is a procedure to share and review your changes with the original project contributors.

1. Open the upstream repository in the browser using the link [nobl9/writingtest](https://github.com/nobl9/writingtest).

> 💡 The link to the original repository can also be found in the tag line **forked from ...** on your forked repository page. (See the picture under step 5 in [Finding and Forking the Test Repository](#finding-and-forking-the-test-repository) above.)

<img src="clone/10_Click_Pull_Request.png" width="600">

2. Select the **Pull Requests** tab in the repository toolbar. Click **New pull request**.

<img src="clone/11_New_Pull_Request.png" width="600">

3. On the **Compare changes** page select **compare across forks**. Note: the additional **head repository** selector now appears and contains a list of existing repository forks. Select your project in **head repository**, and the branch in **compare** (`master` by default). 

<img src="clone/12_Compare_Across_Forks.png" width="600">

4. Review the changes corresponding to the selection. Then click the **Create pull request** button.

<img src="clone/13_Compare_Changes.png" width="600">

5. Fill out the pull request **Title** and **Comment**. Finally, select either **Create pull request** or **Create draft pull request** to complete the pull request.

> 💡 If a draft pull request is created, you have an opportunity to preview and edit the request before the final submission.

<img src="clone/14_Comments.png" width="600">

Congratulations! You have successfully completed forking a GitHub repository and creating a pull request.

## Additional Resources

The following are extra resources to help you with further information.

1. [Getting started with GitHub](https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github)
2. [Working with forks](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/working-with-forks) in Github Docs
3. [Getting changes from a remote repository](https://docs.github.com/en/free-pro-team@latest/github/using-git/getting-changes-from-a-remote-repository#cloning-a-repository)
4. [Pushing commits to a remote repository](https://docs.github.com/en/free-pro-team@latest/github/using-git/pushing-commits-to-a-remote-repository)
5. [Creating a pull request from a fork](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request-from-a-fork)

For GitHub Pages
