# Git Tutorial 

This tutorial operates under the following assumptions

- OS: Ubuntu or some Linux Flavor 
- Git Version: 2.34.1 or later
- You have created a GitHub account at the following link <href>https://github.com/</href>


## Why Do We Use Git and Where?

Git is a *version control platform*, meaning that it is used to synchronize code changes in the cloud. This could be for multiple reasons, such as an emergency backup or for collaborating with others.

Git is used by 99% of the tech industry, as it is widely supported and allows for a secure way to store code in the cloud where it can be modified and re-uploaded by developers.

## Why Should You Use Git

Git is a clean way to backup code, and it also allows for you to write code from multiple devices. 

As previously mentioned, Git is a tool that will be around for a long time, and it is used by almost every tech company, so its a good skill to have! 


## Installing Git

Open a terminal and type the following commands individually:

The below commands are for updating your package manager, *apt* and for installing the Git-CLI (Command-Line Interface)

```
sudo apt-get update
```
``` 
sudo apt-get install git
```
----
The below commands are for configuring your global configuration file: ```~/.gitconfig```.  
Replace your_email with the email you used to create your git account.  
Replace your_name with your name. 
```
git --config user.email your_email
```
```
git --config user.name your name
```

Now you should all of your basic configuration setup, now we are going to work on initializing a repository and setting up your ssh key.


## SSH-Key

SSH  (Secure Shell) keys are encrypted keys that are used in order to remotely access secure servers.

This will be the primary method of accessing a remote Git repository.


### Creating an SSH Key Locally

Create a new SSH key

```
 ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Press ```enter``` to choose the default file name/location.

Press ```enter``` again to keep a blank password.

Press ```enter``` one last time to confirm this password.

This sequence will create two new files in the ~/.ssh directory: 
``` id_rsa ``` (private key) and ```id_rsa.pub``` (public key).

Start the SSH agent

```
eval "$(ssh-agent -s)"
```

Add your new key to the SSH-agent

```
ssh-add ~/.ssh/id_rsa
```

### Link SSH Key to Github account

After you have created this SSH key type the following command and copy the output of the following command:

```
cat ~/.ssh/id_rsa.pub
```

Then open a browser and sign into <href>https://github.com/</href>

Once you've signed in, click on your profile in the top right corner and select **Settings**

![Landing Page](Images/Landing_Page.png)

Once you have selected **Settings**, you will see a page that looks something like this:

![Settings Page](Images/Settings.png)

Click on **SSH and GPG Keys** and then **New SSH Key**. Your screen should look like this: 

![SSH-Key](Images/SSH-Key.png)

Paste the output of this command to the **key** field, give the key a name,
and click **Add SSH Key**.

Once you've linked these two keys, open a terminal and type 

```
ssh -T git@github.com
```

You should see an output that looks like this:

```
Hi User! You've successfully authenticated, but GitHub does not provide shell access.
```

Now you have an SSH key setup for remote access to repositories!


## Branches

Branches are one of the two main concepts of Git.

In every repository, there is a **primary branch**, sometimes called the **main** or **master** branch, varying from repository to repository. 

Picture a branch as a horizontal line, with a plethora of dots plotted on it. Each dot on the branch is called a **commit**. Commits are simply code changes that are added to the end of a given branch. All of the code changes ever made in a repository are reflected in branches.

**You can (and should) branch off of the primary branch.** Your branch originates from a given commit in a repository and runs **parallel to the primary branch.** Doing this allows you to make changes to the code base without them being made in the primary branch, while still keeping up with the changes made in the primary branch. **You can experiment with your changes and test them separately from the primary branch, on your own branch.**

You can create a new branch with the following command:

```
git branch <branchName>
```

You then need to "check out" the branch, switching your local file structure and files to match the branch, so your changes and future commits affect your new branch as opposed to the primary branch. You can do so with the following command.

```
git checkout <branchName>
```
Return to the primary branch at any time with the command:

```
git checkout <primaryBranchName>
```

Note that there are two types of branches, **local branches** and  **remote branches**. Local branches are simply that, local to your machine, and they can be linked to remote branches. Remote branches are located on the GitHub servers, and contain the changes that you push to them.

As mentioned before, you can interact with branches in many different ways. Below are the basics.

### Committing

When you make changes locally, they will be reflected in your local environment.


### Adding 

When you 

## Repositories
### Overview

Repositories (repos) are the foundation of git. There are the 'hubs' of code that contain all of the remote branches related to a given project.

Think of them as a remote folder for all of your files.

#### There can be a local and a remote version of a repo. ####

Local changes to a repo will not be reflected in the remote repo until the changes are pushed to the remote. 

### Creating a Remote Repo ###

Navigate to <href>https://github.com/</href> and sign in.

Click the **New** shown below to start the creation of a remote repository

![Create-Repo](Images/Create_Repo.png)

You can either create the local or remote repo first, but either way, you need to have the two created in order to link them.

Name your repo **2404-github-tutorial**, and give it a proper description. 

For the purpose of this tutorial, you are going to create a **private repository**.

Now that you have created your remote repository, you are going to want to **clone a local copy of this repo** so you can make changes. 

From the directory of your choosing, enter the following commands to create a file in your repo and push them to the remote.

```
echo "This is my first repo!" >> README.md
```
^ Creating a file and writing a line.

```
git init
```

^ Initializing the local repo

```
git add README.md
```

^ Staging our local changes to our "commit" (the changes we push to our remote repo)

```
git commit -m "Created file and added a line"
```

^ We added our changes to the commit, and now we bundled them in a commit, with a message attached, using the -m flag. Keep these simple, but clear.


```
git branch -M master
```

^ Creates our master branch, the branch that is the most up-to-date version of your project

```
git remote add origin git@github.com:<gitUserName>/<repoName>.git
```

^ Linking the local and remote repos to each other using the SSH key we made earlier, and naming it "origin" when referenced from the local environment

```
git push -u origin master
```

^ We push our local branch to the remote master branch, and set it as our upstream branch, meaning that from now on, when we push to our local master branch, the changes will be reflected in the rmeote branch as well





