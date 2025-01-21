# Week 1 Learning

- [Week 1 Learning](#week-1-learning)
  - [Git Fundamentals](#git-fundamentals)
    - [Git Workflow](#git-workflow)
    - [Key Commands](#key-commands)

## Git Fundamentals

### Git Workflow

A git project has three parts:

* `working directory`: where files are created, edited, deleted and organised.
* `staging area`: where changes that are made to the working directory are listed.
* `repository`: where git permanently stores changes as different versions of the project.

The git workflow consists of editing files in the working directory, adding files to the staging area, and saving changes to a git repository.

### Key Commands

* `git init` to initialise a git repo.

* `git Status` to see current status of the repository.

* `git diff filename` to display differences with working directory and the staging area for that file. Use to ensure changes are what you expect before staging.

* `git commit -m "commit message"` creates a new version of the project with the current contents of the staging area, including the log message specified. Last step of the git workflow.