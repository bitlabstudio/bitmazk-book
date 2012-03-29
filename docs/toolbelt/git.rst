Git
===

* create .gitconfig

::

    [color]
        diff = auto
        status = auto
        branch = auto
    [alias]
        st = status
        ci = commit
        co = checkout
        br = branch -all
        log1 = log --pretty=oneline --abbrev-commit
        lg = log --graph --pretty=format:'%Cred%h..%Creset - %s %Cgreen(%cr)%Creset - %an' --abbrev-commit --date=relative
    [merge]
        tool = meld
    [rerere]
        enabled = true
    [core]
        editor = nano
        excludesfile = ~/.gitignore_global
    [user]
        name = Prename Surname
        email = user@example.com
    [http]
        sslverify = false

* .gitignore_global

* create your profile
* create your ssh key
* add your ssh key to your profile
* how to create a repo
* how to add a new file to the repo
* how to commit
* how to push (-u)
* how to remove a file from the repo
* how to add a submodule (init and update)
* how to update an existing submodule
* how to remove a submodule
* how to create feature branches
* how to rebase master into feature branches
* how to merge --no-ff feature branches into master
* how to delete history with gitk
* how to solve merge conflicts with meld

Workflow
--------

* git init -> creates new git repo
* add some files
* git add .
* git commit -am "Initial commit"
* git co -b branch_name -> creates new feature branch
* implement new features
* git add .
* git commit -> add as many commits as you want

A new day dawns:

* git co master
* git pull -> get latest code from team members
* git co feature_branch_name
* git rebase master --> pull in code from team members into own branch and fix
  merge conflicts with ``git mergetool``

When you are done with the feature:

* codereview.sh master -> like git diff master
* git co master
* git merge --no-ff feature_branch_name
* git st --> does everything look good?
* git br -D feature_branch_name --> a merged branch can immediately be deleted
