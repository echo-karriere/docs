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

### Working locally

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

### Committing

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
   
### Pushing
   
We're now ready to push to our repository and create a new pull request. Simply
run `git push -u origin add-git-documentation` and you will automatically create
a new branch on the remote called `add-git-documentation`. This might be named
something other than what you branch is locally. The `-u` flag tells `git` that
it should associate the two branches together.

```git
❯ git push -u origin add-git-documentation
Enumerating objects: 13, done.
Counting objects: 100% (13/13), done.
Delta compression using up to 12 threads
Compressing objects: 100% (8/8), done.
Writing objects: 100% (9/9), 51.39 KiB | 25.70 MiB/s, done.
Total 9 (delta 4), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (4/4), completed with 4 local objects.
remote: 
remote: Create a pull request for 'add-git-documentation' on GitHub by visiting:
remote:      https://github.com/echo-karriere/docs/pull/new/add-git-documentation
remote: 
To github.com:echo-karriere/docs.git
 * [new branch]      add-git-documentation -> add-git-documentation
```

### Pull requests and GitHub Projects

You can use the link in the response from the `remote` to create the pull
request. It will look something like this:

<figure>
  <img src="/images/github-create-pr.png" />
  <figcaption>The pull request view, note that I assignmed myself, added a label and added the PR to the development project board.</figcaption>
</figure>

<figure>
  <img src="/images/github-close-issue.png" />
  <figcaption>You can also hover over the <code>Closes</code> text and see that this will close our first issue.</figcaption>
</figure>

Next up is adding someone to review your code, this should happen automatically
once people start committing code, but you can manually assign someone to the
pull request. In this case I'll add Marie as a reviewer. Your reviewer will look
over the code and might come with suggestions or request changes.

<figure>
  <img src="/images/github-add-reviewer.png" />
</figure>

In this case Marie requested some changes, which you may or may not agree with.
Time to hash it out by discussing why you did things the way you did. 

<figure>
  <img src="/images/github-review.png" />
</figure>

!!! tip 
    Just remember to be nice. Code reviews can feel personal and intimidating, but it's
    done both to learn and help our code stay maintainable.
    
As we can see on our project board, the card now moved to the `Review in
progress column`. Once you're done with the requested changes, you can ask the
person to review the pull request again. Or you might skip this entire step if
everything looks peachy and the pull request is approved immediately.

<figure>
  <img src="/images/github-approved.png" />
</figure>

This is, again, automatically reflected on our development board.

<figure>
  <img src="/images/github-review-approved.png" />
</figure>

You are now ready to merge your pull request!

<figure>
  <img src="/images/github-merge.png" />
</figure>

!!! attention
    Pay close attention to the type of merge you're doing! In this case
    it will automatically be a regular merge, we prefer rebasing over merging
    in our projects.
   
Select `Rebase and merge` from the dropdown to the right of the merge button. Or
follow the instructions you are given in the pull request, occasionally we might
want to squash instead if we have a bunch of temporary commits that we don't
want to litter the history with.
   
<figure>
  <img src="/images/github-merge-types.png" />
</figure>

You'll be given a confirmation before merging so if you accidentally press the
merge button, no worries. You can also change the message, but this should be
wholly unnessecary.

<figure>
  <img src="/images/github-merge-confirm.png" />
</figure>

Once your pull request is merged it and its linked issue will automatically be
moved to the `Done` column of our project board, and you can see in the history
that we now have a commit from our branch.

<figure>
  <img src="/images/github-done.png" />
</figure>

<figure>
  <img src="/images/github-merge-commit.png" />
</figure>

### The end

Huzzah, you have now gotten code into the main development branch, now go to the
top and repeat :smile:

[issuesyn]: https://docs.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword
