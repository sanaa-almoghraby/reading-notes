##  what is Git? ##
* Snapshots
       Git is a DVCS that stores data in a file system made up of snapshots. Each time you save a changed version of your project — called commit — Git creates a snapshot of the file and stores a reference to it. If the file has not changed, Git only stores a reference to the already-stored identical version of it.

* Local Operations
    Git mostly relies on local operations because most necessary information can be found in local resources
* Tracking Changes
     Git will always detect file corruption or loss of information in transit.
* Loss of Data
     Git makes it extremely difficult for a snapshot of your file that is committed to be lost.
* States
    Files in Git can reside in three main states: committed, modified and staged.
## some courses in Git ##
 1.[courses in Git](https://www.udemy.com/course/git-github-crash-course/)
 2.[courses in Git](https://www.udemy.com/course/git-and-github-bootcamp/)
## Download Git ##
   **Linux**
      * Package Manager
                 You can try installing Git via your distribution’s inherent package management tool.

                  For Fedora:

                  $ sudo yum install git
                  For Ubuntu:

                  $ sudo apt-get install git
     
      
   * Git Website
        [To download Git for Linux](http://git-scm.com/download/linux)
        
        
## Setting up a Git Repository ##  
   1.Switch to the target project’s directory
   2.Use the git init command
   3.To start tracking these repository files, perform an initial commit by typing the following
## Workflow ##
   **Local Repository Structure**
       ![ local Git repository ](https://blog.udemy.com/wp-content/uploads/2015/08/image036.png)
## Check File Status ##
     To determine the state of files, utilize the git status command:

     $ git status     
 ## Committing a File ##
      After staging one or multiple files
## Renaming/Removing Remotes ##
      To rename a remote’s short name   
## Pushing ##
      To push your changes “upstream” for sharing
# Undoing Actions #
  * Commit Mistakes
      You can use the –amend command when you need to alter a commit message or forgot to add some files.
  * Unstaging a File
  
  * Undo a Committed Snapshot
     To undo changes resulting from a particular commit,
  * Unmodifying a File
     To have a file return to its state when you last committed
## Branching ##
   ![Branching](https://blog.udemy.com/wp-content/uploads/2015/08/image016.png)
## Creating a New Branch ##
  ![New Branch](https://blog.udemy.com/wp-content/uploads/2015/08/image027.png)
## GitHub ##  
    As previously mentioned, GitHub is a hub-focused tool which facilitates Integration-Manager Workflow. It is the largest existing host for Git repositories and is used by millions of developers worldwide. A high percentage of Git repositories reside on GitHub, and this resource is used by many open source projects.
## Merging ##
**Fast-Forward Merging**
![Merging](https://blog.udemy.com/wp-content/uploads/2015/08/image054.png)
## Log ##
   You can utilize the git log command to view committed snapshots. 
   You can use the command to see a project’s history, use a filter, and find specific modifications.
