gitest
======

This repository is used to sort key concepts and test all kinds of usage or
workflow around git so as to help me grasp this tool.

branch
------

* Commit object

  + `Single commit repository data`_
  + `Git object data for multiple commits`_

* A branch is just a lightweight movable pointer to a commit object, usually
  points to the last commit, every time when commit, it moves forward
  automatically.

  `Branch pointing into the commit data’s history`_

  When create a branch, a new pointer is created, use **git branch**.

  `git branch testing`_

* A HEAD is a pointer of pointer, pointing to the local branch the user is
  currently on.

  `HEAD file pointing to the branch you’re on`_

  To switch to an existing branch, use **git checkout**
  `git checkout testing`_

see [ref.1]_

nvie branch model(workflow)
---------------------------
1. `a successful git branching model`_ (gitflow workflow)
2. `practice in detail on gitflow workflow`_



.. _`Single commit repository data`:
   http://git-scm.com/figures/18333fig0301-tn.png
.. _`Git object data for multiple commits`:
   http://git-scm.com/figures/18333fig0302-tn.png
.. _`Branch pointing into the commit data’s history`:
   http://git-scm.com/figures/18333fig0303-tn.png
.. _`a successful git branching model`:
   http://nvie.com/posts/a-successful-git-branching-model/
.. _`practice in detail on gitflow workflow`:
   https://www.atlassian.com/git/workflows#!workflow-gitflow
.. _`git branch testing`: http://git-scm.com/figures/18333fig0304-tn.png
.. _`HEAD file pointing to the branch you’re on`:
   http://git-scm.com/figures/18333fig0305-tn.png
.. _`git checkout testing`: http://git-scm.com/figures/18333fig0306-tn.png
.. [ref.1] http://git-scm.com/book/en/Git-Branching-What-a-Branch-Is
