# Git

## Tools

This tutorial will use the command line to work through the example, though this
could just as easily be done with the integrated `git` tools in either VSCode or
in one of the JetBrains' products.

## Workflow

It's recommended that you're somewhat familiar with working with `git` before
reading this documentation, see our [learning resources](/resources/learning/)
for a short introduction. What follows is a fairly quick introduction to how to
use issues from Clubhouse, creating a new branch and a pull request to getting
it merged. Aka the full flow of the workflow.

### Selecting an issue

Start by looking for relevant issues on the story board, and then prioritize
issues with labels. You can filter there views in the sidebar by creating a
filter of what you want to show, e.g. only stories for the frontend project with
a label of `high` or `medium` importance.

Once you've found an issue in the `Ready for Development` column you can
drag-and-drop it into the `In Development` column. This will automatically
assign the story to you.

!!! note 
    Be careful to only select from the `Ready for Development` column, the
    `Unscheduled` column is for stories that are not yet ready to start on.

<figure>
  <img src="/images/clubhouse-find-issue.png" />
  <figcaption>Finding an issue</figcaption>
</figure>

Once you've found a relevant issue and dragged it to the correct column, you
will be assigned as the author for this story and you are now ready to start
working on it.

<figure>
  <img src="/images/clubhouse-drag-n-drop.png" />
  <figcaption>You're now ready to start developing</figcaption>
</figure>

### Working locally

Now you're ready to start working on the issue locally. The first thing to do is
to make sure you're on the `master` branch of the repository and that you have a
clean slate and that you're up to date with the `origin`.

!!! tip
    Use the following commands to get started:
    
    ``` git
    ❯ git checkout master
    Switched to branch 'master'
    Your branch is behind 'origin/master' by 26 commits, and can be fast-forwarded.
      (use "git pull" to update your local branch)
    ```
    
    Then run `git pull` to get the latest changes, if you have files that are not
    yet committed or you want to remove, you can either stash them or run `git
    checkout -- <filename>` to erase the local changes.
    
    ``` git 
    ❯ git status
    On branch master
    Your branch is up to date with 'origin/master'.

    nothing to commit, working tree clean
    ```
    
    You are now ready to begin.
    
Next, select the story to be taken into the details view and click on the `git`
helper in the upper right corner.

<figure>
  <img src="/images/clubhouse-git-helper.png" />
  <figcaption>Helper menu</figcaption>
</figure>

Copy the contents of the bottom text area and paste it into your terminal. If
you're using a GUI, copy the proper branch name from the upper text area and use
it to create a new branch.

``` git
❯ git checkout -b feature/ch92/update-documentation
Switched to a new branch 'feature/ch92/update-documentation'
```

You can now start working on your feature/bug fix.

``` git 
❯ git status
On branch feature/ch92/update-documentation
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   docs/common/git.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	docs/images/clubhouse-drag-n-drop.png
	docs/images/clubhouse-find-issue.png
	docs/images/clubhouse-git-helper.png

no changes added to commit (use "git add" and/or "git commit -a")
```

Here we can see that `git.md` file has been changed and that there are at least
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
