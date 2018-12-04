# Git Workflow

### What is Git? 

Linus Torvalds, the creator of Git, described the tool as a ‘stupid content tracker’.He said, “…you can just see git as a filesystem — it’s content-addressable, and it has a notion of versioning, but I really really designed it coming at the problem from the viewpoint of a filesystem person…” That's not suprising after all he was the creator of Linux Kernel. 

### Why Git? 

1.automatic backup of the whole repo: everytime someone pulls from the central repo, he/she gets a full history of the changes. When one repo gets lost: don't worry, take one of those present on every workstation.

2.offline repo access: when I'm working at home (or in an airplane or train), I can see the full history of the project, every single checkin, without starting up my VPN connection to work and can work like I were at work: checkin, checkout, branch, anything.


## So, let's Dive in: 

We will be creating a new github repo to do so click on [github](https://github.com/) 

*Note:* I am assuming that you already have created a github account and you're logged in and that you have git installed on your command prompt

1. We are going to first create a repo (for a sake of this demo I am keeping it simple, so I went with an open project - you have the ability to restrict it to your organization only by choosing private)
![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543944779/github-example/github1.png)
2. We are going to give our repo a name and initialize it with a readme ![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543944801/github-example/github2.png)
3. In this step we are going to invite members of our team to join and collaborate![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543944820/github-example/github-settings.png) ![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543944843/github-example/github-s-1.png) ![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543944872/github-example/github-s-2.png) ![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543944872/github-example/github-s-2.png)  
Before diving in and start using git commands let's see how we can protect people from pushing to master branch (side note: Most of the time master host production code)

4. We are going to create a rule that would prevent members of the organization from pushing code directly to the master branch  
 ![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543944909/github-example/github-s-4.png)  ![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543944927/github-example/github-s-5.png) ![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543944942/github-example/github-s-6.png)
 
 ### Congrats we finished setting up our project! 
 
 ## Now let's start using git
  
  First let's open the terminal and navigate to the directory where you want to keep you project for me it's going to be `~/Desktop/dev`  
  ```shell
	cd ~/Desktop/dev
  ```
  
  we are going to clone the repo in our local machine and for the we would need the link to our github repo ![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543949510/github-example/git-clone.png)
Now that we have the link copied let's go back to the terminal and run the following command
  ```shell
git clone <github-repo-url>
```
Once you are done cloning the repo go inside our project directory

```
ls
// => github-example
cd github-example
```
Since it is a good practice not to push your code to master, we will be creating what we call a feature branch (to keep our development code separated from the production one). To do so we are going to use `git branch` to see what our current head (for us it should return master since we created a new project)
```
git branch 
// => master
  ```
Create a branch using the following naming convention in the terminal.

  ```shell
  $ git checkout -b "<feature-branch>"
  // => The convention is to name your branch after the feature you're currently working on 
  $ git branch
  // => should return <fature-branch>
  ```

Let's open the readme file with your favorite text editor I will be using vim from the command line, but feel free to use editor of your choice


  ```shell
  $ vim README.md 
  ```
press on a letter `i` in the keyboard to insert (add/edit or delete) a line and you can add something of your choice. Once you're done press escape and enter `wq` (for write and quit) 
  
When you work in production env you may make changes to different files and it's hard to keep track that's when git comes in handy. Let's how we it's done:

 ```shell
  $ git status
 
// git status => returns all the files that where changed, deleted or added 
// And the message should say Changes not staged for commit: README.md
  ```
  
  In our case it's going to return `You've modify README.md file please commit your changes`. So now we need to add it to git control:

 ```shell
  $ git add README.md //(or the name of the file that was modified)
  ```
  Now let's check the status again: 
   ```shell
  $ git status
 // =>  Changes to be committed: README.md
  ```
  At this point we just need to commit and push our branch to our github repo: 

   ```shell
  $ git commit -m "Add github links to readme.md file" // -m stands for message 
 // =>  Changes to be committed: README.md 
  ```
  Commit messages should start with a verb, use present tense, and describe the work you have done. 
  
 ## Final step
 
 Our final step is to push our current branch to github and open a pull request tagging the project owner to review your changes:
 
 ```shell
  $ git push origin feature-branch 
  
  // => when it's done successfully you should see 
  // Writing objects: 100% (8/8), 1.03 KiB | 350.00 KiB/s, done.
  // Total 8 (delta 6), reused 0 (delta 0)
  // remote: Resolving deltas: 100% (6/6), completed with 6 local objects.
  // To https://github.com/bon-heur/github-example.git
  // 2308295.80308294..120c778d1  branch -> feature-branch
  ```
  
  - Let's go back to our github repo and open our first pull request: 
  
  step 1: 
  ![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543960080/github-example/pull1.png)
  
  step 2:
  ![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543960080/github-example/pull2.png)
 
  step 3:
   ![alt text](https://res.cloudinary.com/dcqrxsgq8/image/upload/v1543960080/github-example/pull3.png) 
  
  
  Congrats ! Now you have first git workflow. Below are some good links for best practices with git. 
  
