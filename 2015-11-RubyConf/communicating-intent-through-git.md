# Communicating Intent Through Git
Josh Freeman @joshFreemanIO
Grok Interactive - In San Antonio
11/16/2015

## Stories Have Power

Data Compression exists in video, music, etc.  But when communicating intent, it is bad

If you compress too much you lose the narative

## Why do we use git?
![xkcd.com/1597](xkcd comic)

* Transferring files via ftp, etc is dumb
* We need iterative improvement

*Git a communication tool*

## Software has 3 audiences

* Author
* Team
* Future maintainers

Software evolves and we should know why these changes are made.

Two hard problems in software

* Naming things
* cache invalidation
* one off errors

Comments are an apology, if we are commenting a lot it is probably an apology for poor naming.

Large chunks of comments in code might be better served as a commit message.

![http://xkcd.com/1296](xkcd comic)

## How can we use git to be better communicators?

Do not use

    git commit -m

You should not be trying to be as brief as possible.

Write imperitively in 50 characters or less <-- from Tim Pope article

## The Message

Provide a detailed message, keeping lines under 72 chars in length for people using terminals

Answer the following questions in your commit message:

* Why is this necessary
* How does this address the issue?
* What are the side effects?
* References and resources

One way to make this easy is to create a ~/.gitcommittemplate from above.

This will pre-populate into your commit messages if you connect to it in your ~/.gitconfig

[user]
    name =
.
.
.
(link to template)

### This is useful in blame game
But blame is a bad word for this, Josh aliased blame as "thank"

When you look back in time at a change in code, neither the other person, nor you will know why you did things if you do not have a good commit message.

* Include email requests for reference
* Include full url of ticketing system

To search log

    git log --grep="favicon"

To separate individual changes when multiple have been added

    git add --patch

Split (s option) will break large hunks into smaller hunks

The following will diff on only the staged changes

    git diff --cached

If split does not work, you can use edit (e option) to manually stage hunks.

Ok sometimes you do not need a full message (spelling corrections, objious things)

Ok to note, changes that might want to have in the future.

## Do not fear the rebase

To fix error message in previous commit

    git rebase -i 0964dd6~ 1

## Successful git branching model

http://nvie.com/posts/a-successful-git-branching-model

He had been moving dev branch to master (prod) every few weeks or months, this was bad because there was a lot of code to move and the purpose of the code was not fresh in his mind.

### New way

* master (prod)
* devel
* +feature branches

Once the branch is merged with devel and approved, it gets pushed to prod on quick turnaround.

## Pull Requests

Keep them small and focused

## LICEcap is your friend

cockos.com/licecap

The gif from LICEcap will drastically reduce the number of demos you will have to do because it will be understood.

## Code Reviews

Where it all comes together

Should be in person if possible, or video.  Adds personal element and reduces tension and shares knowledge.

Having good commit messages will help communicate intent and clarify your pull requests making your code easier to review.

Be nice

## Take Away

git add --patch
do not use add -m
Be excellent to each other
