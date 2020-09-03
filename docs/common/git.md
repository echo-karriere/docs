# Git

## Tools

This tutorial will use the command line to work through the example, though this
could just as easily be done with the integrated `git` tools in either VSCode or
in one of the JetBrains' products.

## Workflow

It's recommended that you're somewhat familiar with working with `git` before
reading this documentation, see our [learning resources](/resources/learning/)
for a short introduction. What follows is a fairly quick introduction to how to
use issues from the project board and automatically close it with a pull request
in GitHub.

### Selecting an issue

Look at the top of the issue board on GitHub for an available task in the `To
do` column, the higher it is the more prioritized it is, so it's prefered that
you try to select relevant issues from as high as possible.

<figure>
  <img src="/images/git-select.png" />
  <figcaption>Selecting an issue</figcaption>
</figure>

Once you've found a relevant issue, assign yourself by clicking the `assign
yourself` text, it should now display your avatar and name.

<figure>
  <img src="/images/git-assign.png" />
  <figcaption>Assigning yourself to an issue</figcaption>
</figure>

Now you're ready to start working on the issue locally, to do so check out the
repository on your machine and create a new branch with a relevant name for what
you're working on: `git checkout -b add-git-documentation`. After a while you
might be ready to commit your changes so you run `git status` to see what has
changed and what hasn't:

``` git 
❯ git status
On branch add-git-documentation
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   mkdocs.yml

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	docs/common/
	docs/images/git-assign.png
	docs/images/git-select.png

no changes added to commit (use "git add" and/or "git commit -a")
```

Here we can see that `mkdocs.yml` has been changed and that there are at least
three new untracked files (i.e. files that did not exist before this commit). If
you think everything is fine you can add everything, but this is not a healthy
habit as you *will* end up accidentally adding and pushing things you didn't
mean to.

We will be risky and add everything at once; `git add .`. Running `git status`
again now shows that we have changes added.

```git
❯ git status
On branch add-git-documentation
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   docs/common/git.md
	new file:   docs/images/git-assign.png
	new file:   docs/images/git-select.png
	modified:   mkdocs.yml
```

We can now commit our changes and push them to a new branch on the remote
server. You can either commit by running `git commit` and it'll open a window of
whatever `$EDITOR` is set to on your OS. On Linux it'll either open in `nano` or
in `vim` for example, while on macOS it might be something else. Or you can
commit by using the `-m` flag: `git commit -m "Message"`.


```git
❯ git commit -m "Add documentation for using Git

  Closes #1"
[add-git-documentation 145adb3] Add documentation for using Git
 4 files changed, 87 insertions(+), 2 deletions(-)
 create mode 100644 docs/common/git.md
 create mode 100644 docs/images/git-assign.png
 create mode 100644 docs/images/git-select.png
```

!!! note 
    The syntax for automatically closing issues on GitHub can be found
    [here][issuesyn]. You'll find the issue number by looking at the title of
    the issue on GitHub.
    
We're now ready to push to our repository and create a new pull request. Simply
run `git push -u origin add-git-documentation` and you will automatically create
a new branch on the remote called `add-git-documentation`. This might be named
something other than what you branch is locally. The `-u` flag tells `git` that
it should associate the two branches together.
    
[issuesyn]: https://docs.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword
