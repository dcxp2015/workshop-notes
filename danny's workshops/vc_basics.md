## Version Control Basics
Here you'll find a workshop on the basics of using version control for everyday projects, tailored towards Git.
#### Key Takeaway
Version Control is important (read: necessary) for any sort of project you write with more than one developer, and incredibly useful for independent projects as well. So long as you commit early and commit often, you'll never run into issues of code loss and will be able to easily share, document, and revert any project changes.
#### What is Version Control?
Version Control is a means by which a project's history and revisions are stored for later access. All of this information is stored in what's called a *repository*. This repository can live either on a local machine or online somewhere. Services that allow for the creation of these repositories include, but are not limited to, [Git](https://git-scm.com) and [SVN](https://subversion.apache.org). Applications such as [GitHub](https://github.com) and [Bitbucket](https://bitbucket.org) make these repositories come alive by providing a network to host and share these repositories, both privately and publicly. We'll be using GitHub for our projects here in DCxP, so this workshop will focus on the effective use of GitHub and Git for team projects. 
#### How can I start?
The first step is to create a new repository. You can create one straight form GitHub. This repository doesn't actually need to be hosted online, but we'll be keeping most of our projects here. There are already some repositories setup for you to start your projects for the first couple days. Once you have a repository you wish to access, you can clone it to your local machine using either the command line or a git interface app. On command line, you just move to the directory in which you wish to clone the project, then enter the following:
```
git clone http://github.com/user/repository
```
If you do choose to use an interface, I personally recommend [SourceTree](https://www.sourcetreeapp.com), as it lets you have control exactly which lines get synced with each change. From SourceTree, you just need to connect an account (either GitHub, BitBucket, or Stash) and you can start cloning projects directly from your remote account. I'd recommend that you keep all of the projects you clone in separate folders within one larger workspace folder. This will help you keep all the projects using version control organized. You should familiarize yourself with
#### Basic Git Concepts
Once you have a copy of a project saved to your local machine, you can immediately start making changes! Each time you wish to store a set of changes, you make what's called a *commit*. A commit will store a set of changes on your local machine. You can then push your changes back up to the remote copy via the push command. Running the pull command will pull down remote changes onto your local version of the project. 
#### General Workflow 
As a general rule, the workflow should go as follows: Commit->Pull->Push

I would also recommend the following two guidelines for git workflow:
- If two or more people are working on independent parts of the projects, work on different branches - it will help you track (and potentially revert) changes easily
- If two people are working on the same file(s), work on the same branch - it will prevent conflicts from building up and becoming unmanagable

#### Additional Reading
Of course, these are just the bare basics. Here are some additional resources for slightly more advanced actions:

- https://www.atlassian.com/git/
- http://stackoverflow.com/questions/315911/git-for-beginners-the-definitive-practical-guide
