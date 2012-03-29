Codereview
==========

* download codereview.sh from bitmazk-environment
* download it into your bin folder and give chmod +x
* URL of codereview tool: http://codereview.bitmazk.com

Workflow
--------

* git co master
* git pull
* git co -b feature_branch
* implement feature until you are happy
* git st
* BEFORE git add . do this:
* codereview.sh
* it will ask you to give a topic
* authenticate with your.name@bitmazk.com and your gmail password
* then go to codereview.bitmazk.com
* open the new issue
* jump through all changes with n and to next file with j
* double click lines where you think they need further explanation
* click at "Publish+Mail Comments" link
* add reviewers (tob, mar)
* add general message if necessary
* git add . && git commit

if you already committed, you can send a codereview like this:

* git lg -> shows all short hashes
* git diff DH8s82S..298SJ2h -> make sure that this is the stuff you want to
  submit
* codereview.sh DH8s82S..298SJ2h -> codereview takes the same parameters as git
  diff

if you already added changes via git add

* git diff HEAD
* codereview.sh HEAD

When someone did the review and found bugs

* go to same feature branch, or start a new one
* implement changes
* codereview.sh -i issue_number
* Topic: Implemented comments by XYZ
* Go to codereview.bitmazk.com
* browse through patch, add comments where needed
* and publish+mail comments

When someone answers with LGTM:
* go to codereview.bitmazk.com and close the issue (via edit link)
