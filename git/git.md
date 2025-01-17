# Git

- [Repositories](#repositories)
- [Working with branches](#working-with-branches)
- [Commit messages](#commit-messages)
- [Pull requests](#pull-requests)
- [Versioning](#versioning)

## Repositories

We use a standard naming format for our Git repositories. Repository names are _lowercase-hyphenated_ (all lowercase, words separated by a hyphen), and begin with "frontend" followed by your project name.

We _don't_ do this:

```
front-end-project-name
front-end-projectname
project-name-front-end
project-name-frontend
```

We do this:

```
frontend-project-name
```

## Working with branches

Create a local branch based off the default branch. For this example, let's assume the default branch is called `main`.

Follow [Continous Delivery](https://martinfowler.com/bliki/ContinuousDelivery.html) and [Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html) principles as much as is reasonable (given the constraints of your team). Branches should be:

* As short lived as possible.
* _Atomic_, i.e. one unit of work that can't be sensibly subdivided.
  * They should contain their own tests.
  * They should be releasable independently.
* As limited in scope as possible. Large pull requests are hard to review and can be painful to merge. Also, once merged & a bug is traced back to that commit, they are much harder to debug.

When your work is almost complete, `git rebase main` or merge -- especially if other people are working on the same code. Avoid merge pain by;

* _talking to your team_ to divide work across files sensibly & co-ordinate merges if required.
* `git pull origin main` and rebase or merge often.
* make sure branches are short-lived! (Did we mention that branches should be short-lived?)

When the unit of work is complete and tests pass, stage your changes and commit them.

## Commit messages

Your commit messages are your personal legacy. They are the record of what you've done to a codebase and more importantly, *why*. A good commit message is composed of a summary line or shortlog, and a description.

* The summary line should be [50 characters or less](http://stopwritingramblingcommitmessages.com/), followed by a blank line.
* Use present tense rather than past tense when referring to changes introduced by commit in question. For example, use "Update request library" instead of "Updated request library". Imagine your commit message has to make sense prefaced with _"If applied, this commit will..."_.
* Summarize only the change itself in the summary line, not the bug or effects/benefits (that goes in description).
* Unhelpful messages like "Update" or "Bugfix" are... _unhelpful_. Please explain a little more. Bear in mind that the commit message should allow you or anyone else to understand the changes, both now and in a year's time.
* If your work is part of a ticket, include the ticket number in the commit message, but don't only use the ticket number as the commit message. Otherwise this just makes life hard for your colleagues to understand what the change was for. The git log should be all they need to read. You may also include a link to the bug after the description, separated by one blank line.
* Add a description, if necessary, as detailed as you need. Make sure that lines wrap at 72 characters.

A few blog posts on writing better commit messages:

* [5 Useful Tips for a Better Commit Message](https://robots.thoughtbot.com/5-useful-tips-for-a-better-commit-message)
* [A Note About Commit Messages](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
* [Git Commit](http://chris.beams.io/posts/git-commit/)
* [Writing Good Commit Messages](https://github.com/erlang/otp/wiki/Writing-good-commit-messages)
* [Better Commit Messages with a `.gitmessage` Template](https://robots.thoughtbot.com/better-commit-messages-with-a-gitmessage-template)
* [GNOME project - Guidelines for Commit Messages](https://wiki.gnome.org/Git/CommitMessages)

Once your work is committed, submit a [pull request](https://help.github.com/articles/using-pull-requests/).

## Pull requests

We use pull requests to review code. [GitHub's pull request reviews feature](https://help.github.com/articles/about-pull-request-reviews/) blocks merging of code until it's been reviewed. It may or may not be enabled on a repository, at the discretion of the individual team. You should submit your pull requests for review regardless of whether or not this feature is enabled.

1. Ask for a code review in Slack.
2. A colleague (or multiple colleagues) other than the author will review the pull request. They will make comments and ask questions directly in the GitHub web interface. See the [Code review guide](../practices/code-review.md) to see what reviewers are looking for.
3. When satisfied, the reviewer(s) will approve the pull request, so that your code can be merged.
4. Give your code one last visual check in github.
5. Double-check the commit message -- and any commit message detail -- then **"Squash & Merge" commits via github**. We do not want lots of "work in progress" commits cluttering the commit history on the default branch. _One unit of work, one commit._

Your work is now merged, good job! Delete your remote branch, and delete your local branch too, if you want.

## Versioning

Our open source projects are versioned with [SemVer](semver.md). Check our [Open Source support](../practices/open-source-support.md) guide for details on how to version and release an update to an open source project.

Closed source projects may use different versioning practices.
