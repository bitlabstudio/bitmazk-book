Codereview
==========

Currently we use barkeep to review our code.

http://getbarkeep.org/ 


Committing
----------

When the project is added to barkeep, you just push your code and after a few
moments barkeep will have added the commit to the list.

Issues
------

If someone finds something that needs improvement, he will comment on the line 
where the mistake is found. Also if something is unclear, questions will be 
asked in the same manner directly attached to the corresponding lines.

When someone fixes the issue, one comments with "DONE" on the related issue,
so the reviewer knows, that a patch is about to be uploaded. After fixing all
issues one adds a general comment with "fixed in <commit number>" for reference
purposes and to show, that the fixes have been made.

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

Lists in barkeep
----------------

You can create custom filtered lists on barkeep according to different
criteria.

It is advised to have at least a list with unapproved commits of all
branches and repositories and a list of all commits in general, that you can 
adjust to email notifications for new commits and comments.
With this it is easy to keep track of new commits and such that still need
approval.
