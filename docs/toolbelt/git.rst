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

TODO
====
* branches
* merging
* merge conflicts
