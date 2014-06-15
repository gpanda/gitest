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

merge
-----
* fast-forward(ff)

  `ff:before merge`_ and `ff:after merge`_

  When you try to merge one commit with a commit that can be reached by
  following the first commit’s history, Git simplifies things by moving the
  pointer forward because there is no divergent work to merge together — this
  is called a "fast forward". **No commit created.**

* basic merge

  `basic:before merge`_ and `basic:after merge`_

  Git creates a new snapshot that results from this three-way merge and
  automatically **creates a new commit** that points to it. This is referred to
  as a merge commit and is special in that it has more than one parent.

  Git determines the best common ancestor to use for its merge base; this is
  different than CVS or Subversion (before version 1.5), where the developer
  doing the merge has to figure out the best merge base for themselves. This
  makes merging a heck of a lot easier in Git than in these other systems.

* handle conflicts

  Automatic merge failed; fix conflicts and then commit the result.

  git status

  Git adds standard conflict-resolution markers to the files that have
  conflicts, so you can open them manually and resolve those conflicts, or use
  (git mergetool).

  conflict section looks like:

  <<<<<<< HEAD (current branch)
  abcd
  =======
  1234
  >>>>>>>> <branch-to-merge>

  After fix the conflict, git add and git commit.

see [ref.2]_

rebase
------
* basic rebase

  `basic:before rebase`_ and `basic:after rebase`_

  git checkout experiment
  git rebase master

  It works by going to the common ancestor of the two branches (the one you’re
  on and the one you’re rebasing onto), getting the diff introduced by each
  commit of the branch you’re on, saving those diffs to temporary files,
  resetting the current branch to the same commit as the branch you are
  rebasing onto, and finally applying each change in turn.

  At this point, you can go back to the master branch and do a fast-forward
  merge. `Fast-forwarding the master branch. Basic.`_

* advance rebase

  `advance:before rebase`_ and `advance:after rebase`_

  git rebase --onto master server client

  Check out the client branch, figure out the patches from the common ancestor
  of the client and server branches, and then replay them onto master.

  Now you can `fast-forward your master branch. Advance.`_

  git checkout master
  git merge client

* git rebase [basebranch] [topicbranch]

  You can rebase a topic branch onto a base branch without having to check it
  out first by running git rebase [basebranch] [topicbranch] — which checks out
  the topic branch for you and replays it onto the base branch.
  `Rebasing your server branch on top of your master branch`_

  git rebase master server

* **Do not rebase commits that you have pushed to a public repository.**

see [ref.3]_

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
.. _`ff:before merge`: http://git-scm.com/figures/18333fig0313-tn.png
.. _`ff:after merge`: http://git-scm.com/figures/18333fig0314-tn.png
.. _`basic:before merge`: http://git-scm.com/figures/18333fig0314-tn.png
.. _`basic:after merge`: http://git-scm.com/figures/18333fig0317-tn.png
.. [ref.2] http://git-scm.com/book/en/Git-Branching-Basic-Branching-and-Merging
.. _`basic:before rebase`: http://git-scm.com/figures/18333fig0327-tn.png
.. _`basic:after rebase`: http://git-scm.com/figures/18333fig0329-tn.png
.. _`Fast-forwarding the master branch. Basic.`:
   http://git-scm.com/figures/18333fig0330-tn.png
.. _`advance:before rebase`: http://git-scm.com/figures/18333fig0331-tn.png
.. _`advance:after rebase`: http://git-scm.com/figures/18333fig0332-tn.png
.. _`fast-forward your master branch. Advance.`:
   http://git-scm.com/figures/18333fig0333-tn.png
.. _`Rebasing your server branch on top of your master branch`:
   http://git-scm.com/figures/18333fig0334-tn.png
.. [ref.3] http://git-scm.com/book/en/Git-Branching-Rebasing
