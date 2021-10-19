---
title: Rolling Back Commits in Git
layout: post
author: jace899
post-image: "https://raw.githubusercontent.com/thedevslot/WhatATheme/master/assets/images/SamplePost.png?token=AHMQUEPC4IFADOF5VG4QVN26Z64GG"
description: A sample post to show how the content will look and how will different
  headlines, quotes and codes will be represented.
tags:
- revert
- git
- rollback
- commit
---

As all data scientists know, coding can do weird things during routine processes. Whether it's an unexpected data type returning errors on a dataframe method or a regular expression returning an extra space, small changes to code can drastically change the outcome of any project. One of the processes that produces such odd outcomes at an unexpectedly high rate is moving code that functions on a local machine to a production-level application. While these errors can be largely prevented by updating branches with the main repository at least daily to ensure data quality, sometimes small logic errors creep into production that can break downstream models or lead to data loss, both of which can be detrimental to business models. Happily, Git offers many options to quickly remove the offending lines of code until the error can be fixed, thus returning the code to its previously functioning state.

![Dont touch the code](/assets\images\blogimages\figs-10-21\dont-touch-my-code.jpg)

---

# Rolling Back Commits using Git
Note: For all of the following commands, the offending commit needs to be identified in order to remove it. Some help for debugging can be found in this article: [3 Awesome Git Commands](https://www.vinta.com.br/blog/2015/3-awesome-git-commands/).
## Revert
First on the list is `git revert`. The revert command keeps with the idea behind Git that changes should be documented so that collaborators can understand why the code has been changed. In essence, `git revert` reverses the effects of unwanted commits (i.e. adds deleted lines and deletes added lines) through a series of new commits. These new commits ensure that the changes are documented so that other programmers (including future you) know why not to do what was just done. Using `git revert` in its base form is very simple. Just type the command `git revert` followed by the names of the offending commits. For example, suppose that we make the following git repository along with the commits shown.

![initial-stuff.jpg](/assets\images\blogimages\figs-10-21\initial-stuff.jpg)

Now new_file.txt contains 'Stat 426', with a newline after 'Stat'. Now we make an error in our code as shown below.

![error](/assets\images\blogimages\figs-10-21\not-wanted.jpg)

However, stating that Stat 426 is dumb is an undesirable addition to our code and is something we want to get rid of. We will use `git revert` to change it back. We first use `git reflog` to find the commit names, which is fairly simple since our repository is so small. We know that 'commit 3' is the one we want to change, so we use the id associated with it to reverse the changes with `git revert`, as seen below.

![revert-save-day](/assets\images\blogimages\figs-10-21\Revert-saves-day.jpg)

As shown above in the second usage of `git reflog`, there is an extra commit listed that states that we reverted the changes from 'commit 3' because the statement made about the class wasn't true. Now new_file.txt is restored to its previous state, without the false information inside of it.

For more information about `git revert`, see the [git revert documentation](https://git-scm.com/docs/git-revert).

## Reset

While `git revert` is sufficient when the changes made can be traced back to one bad commit, its ability to work with many undesirable changes over multiple commits is limited by the coder's desire to input every single commit id until reaching the commit with the code they want. In contrast, `git reset` excels at such tasks. Instead of reverting changes from one commit, it resets the repository to a specific commit, getting rid of the changes made after the desired commit. For example, consider a repository with a file called 'new_file.txt', as shown below.

![good-reset](/assets\images\blogimages\figs-10-21\good-reset.jpg)

The file 'new_file.txt' now holds desirable code and is committed. However, further material is added and committed as shown below.

![bad-reset](/assets\images\blogimages\figs-10-21\reset-bad.jpg)

While everything may look correct above, upon further inspection there is a mistake. We accidentally overwrote the file and didn't realize it! Now the code is incomplete and incorrect, as shown below.

![realize-reset](/assets\images\blogimages\figs-10-21\reset-realize.jpg)

This kind of situation is where `git reset` is useful. Because the additional code following the overwritten file is incorrect and spans multiple commits, we can't just get rid of the offending code with one `git revert` command. However, we can reset our commits to the functioning code with one command, as follows.

![fix-reset](/assets\images\blogimages\figs-10-21\reset-fix.jpg)

As shown above, the correct code from a previous commit replaced the faulty code, which was the desired effect. However, using this format, there isn't an option to name the commit that records the reset. Notwithstanding, a commit will be made that records the change. For more information about `git reset`, [Click here to check the documentation for git reset](https://git-scm.com/docs/git-reset).

## Restore

While `git revert` and `git reset` work well to restore previous commits, it is often useful to restore previous commits only for certain files instead of rewriting each file the commit touched. This is easily achieved by using `git restore`. While the same function can be fulfilled using `git checkout`, `git restore` tends to be less complicated since it is intended for restoring specific files instead of entire branches, which is why we use it here. However, since the command is still experimental and subject to change, checking the documentation often is highly recommended. [Click here to check the documentation for git restore](https://git-scm.com/docs/git-restore). 

In order to show how it works, consider an example with two files that contain good content. They have been commited as shown below.

![initial restore](/assets\images\blogimages\figs-10-21\restore-begin.jpg)

However, after the first commit, some unwanted content is added. It is subsequently committed, and is now part of our code.

![bad stuff](/assets\images\blogimages\figs-10-21\restore-bad.jpg)

After the undesirable content is added, some desirable content is added and committed as well.

![good stuff](/assets\images\blogimages\figs-10-21\restore-good.jpg)

Now, if we reverted or restored to the first commit, we would lose the desired code in new_file2.txt and need to redo our work! While that would be trivial here, in larger scale cases, such a scenario would most likely mean at least hours of work would need to be redone. Therefore, we will restore only the file with undesirable content to the original commit and leave the other file alone. Using the reflog command to find the commit id, we can use `git restore` to get the original content of the file back.

![final restore](/assets\images\blogimages\figs-10-21\restore-final.jpg)

As shown above, the file with undesirable content was changed back to way it was in the specified commit and our other file was left alone. However, the changes we made are still uncommitted, so be warned!

# Conclusion

Because coding is a large part of data science, every data scientist will make mistakes that will get committed. To think otherwise is naive at best. Therefore, it is important to know how to remove those errors. When those errors get committed to a repository, using  `git revert`, `git reset`, and `git restore` can be extremely useful in bringing faulty new code back to production-level old code.