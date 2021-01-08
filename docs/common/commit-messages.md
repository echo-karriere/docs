# Commit messages

Due to how we manage our projects in a project board on Clubhouse there are
requirements for how we structure commits so that they are properly tracked from
GitHub and Clubhouse. In this doc we'll walk you through how to properly commit.
:smile:

## Style

Commit titles should be short and to the point, and if you are working on a
story should follow a standardized structure:

`[CH-123]: Added foo for bar`
:   If the commit is directly related to a story you should have it at the
    beginning of your message. Note that this is not how Clubhouse wants you to
    format it by default, if you want to know why, see the [why section](#why).

`Fixed mistake introduced in last commit`
:   If your commit do not contain any kind of reference to a story in Clubhouse
    there are no errors and you can proceed as normal.

If you attempt to commit using the wrong commit structure you will get an error
explaining what is wrong:

`Added foo for bar [ch123]`
:   This will fail when you attempt to commit with the following error: `You
    should start your commit message like this: '[CH-123]: <message>'`.
    
`[ch-123]: Added foo for bar`
:   This will fail due to the case sensitivity.

`[CH-123] Added foo for bar`
:   This will fail because of a missing colon after the closing bracket.

# Why

GitHub has a feature called [autolinked references][autolink] that enable you to
reference issues and PRs across repositories and projects. This works very well
inside GitHubs little bubble, but since we use Clubhouse we need to add
[external references][external] to link from GitHub to Clubhouse. Now, on the
other end Clubhouse wants us to use `[ch123]` to track issues, but GitHub (for
whatever reason) require that the reference prefix is at least _three_
characters long... which as you might imagine is an issue.

Luckily Clubhouse supports references with a dash after the `CH`, so we need to
enforce that commits using these references are properly formatted, hence the
need for these guidelines.

[autolink]: https://docs.github.com/en/free-pro-team@latest/github/writing-on-github/autolinked-references-and-urls
[external]: https://docs.github.com/en/free-pro-team@latest/github/administering-a-repository/configuring-autolinks-to-reference-external-resources
