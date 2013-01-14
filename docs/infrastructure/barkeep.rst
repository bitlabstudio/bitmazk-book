Barkeep
=======

We use `Barkeep <http://getbarkeep.org>`_ as our main codereview tool.

The goal is that every single line anyone commits to any master branch in any
of our projects gets reviewed by at least one other team member.

This might sound like a daunting task at first but it actually takes lesser
time than one might think and creates huge benefits in the long run since the
knowledge gets quickly spread from more experienced developers to less
experienced ones.

Settings
--------

After logging in for the first time you should go to ``Settings`` and

* set the line length indicator to 80 characters
* Set your name

Commits View
------------

On this view you can created searches. You should at least have two searches:

* An empty search that shows all commits on all master branches
* A search for ``branches:all`` that shows all commits on all branches

Using the ``Search options`` for both searches you can set ``Only show
unapproved``.

With this setup you can easily see all unapproved commits accross all our
projects.

Whenever you push your commits it will take a few minutes before Barkeep
automatically fetches the commit. You don't need to do anything in order to
upload a commit for review.

Workflow and rules in short
---------------------------

1. No one is allowed to approve their own commits.
2. If you feel unsure about the commit (maybe because you lack the experience)
   but you think that it looks good, do not approve the commit but leave a
   comment ``LGTM`` (Looks Good To Me). Someone else with enough experience
   will approve the commit.
3. If someone else already left a ``LGTM`` and you yourself feel unsure as well
   and you are the last employee to review, you leave a ``LGTM`` as well but
   you also approve the commit.
4. When someone leaves comments for you and suggests improvements, please do
   them in a new commit. The commit message should be ``codereview fixes for
   6jau2hrd``, followed by a more explanatory text of what you changed, so that
   we can still guess from the commit message what has been done, without
   needing to open the referred to commit in barkeep.

Committing
----------

When the project is added to barkeep, you just push your code and after a few
moments barkeep will have added the commit to the list. You can even push your
feature branches to origin and they will show up in barkeep. Of course this
has the disadvantage that all this code will show up again when you finally
merge it. So far it has turned out that we rarely need to work on huge feature
branches.

Issues
------

If someone finds something that needs improvement, he will comment on the line
where the mistake is found. Also if something is unclear, questions will be
asked in the same manner directly attached to the corresponding lines.

When you fixe an issue, reply with "DONE" to the comment that raised the issue.
This way you know how many issues are left and the reviewer knows that a path
with fixes is on its way. After fixing all issues add a general comment with
"fixed in <commit number>" for reference purposes and to show, that the fixes
have been committed.

If a fix is expected to be bigger, it is possible to add a Trello card for the
issue and to link to it in a comment. The issue is then considered as about to
be solved in later commits.

Suggestions
-----------

If there is something, that is not really a mistake but just a suggestion for
improval you add "SUGGESTION" to the comment. Suggestions don't need to be
fixed in the patch set like the regular issues.

Approving commits
-----------------

If all issues are fixed or there were no mistakes at all, the commit can be
approved.

If a reviewer is not 100% sure about the code, but has not found any real
mistakes, he can add "LGTM" for "looks good to me". If the last one to review
the commit would also add a "LGTM" he can just approve the commit, since no
mistakes were found.

But keep in mind, that this can be a hint for the programmer that wrote the
code, that it might need further commenting or better structure, since the code 
was not really understandable to all of his fellow colleagues.


How to add new repos
--------------------

1. SSH into out barkeep server
2. Form there, SSH into the server that contains the repo. You will be asked
   to add that new server to barkeep's ``known_hosts`` file.
3. Add barkeep's public RSA key (``cat ~/.ssh/id_rsa.pub``) to the repo-server's
   ``authorized_keys`` file.
4. Now barkeep should be able to SSH into the server that contains the repo
   without needing a password.
5. Browse to our barkeep instance and go to ``/admin/repos/``
6. Add the new repo
   (``username@username.webfactional.com:/home/username/webapps/git/repos/projectname.git``)
7. Reload the page. The new repo should be shown under the headline
   ``Repos scheduled to be cloned``
8. Reload the page a few more times until the repo is no longer shown under
   that headline. Now scroll down all the way and check in the
   ``clone_new_repo.log`` if it says ``Finished cloning the repo [reponame]``
