# Commit Often, Perfect Later, Publish Once—Git Best Practices

## sethrobertson.github.io

#articles
#pocket

![](https://readwise-assets.s3.amazonaws.com/static/images/article4.6bc1851654a0.png)

[source](https://sethrobertson.github.io/GitBestPractices/)

### Highlights from July 26, 2021

- There are three places where “lost” changes can be hiding. They might be in the reflog (git log -g), they might be in lost&found (git fsck --unreachable), or they might have been stashed (git stash list).
- reflog The reflog is where you should look first and by default. It shows you each commit that modified the git repository. You can use it to find the commit name (SHA-1) of the state of the repository before (and after) you typed that command. While you are free to go through the reflog manually (git log -g) or searching it (git log -Sfoo -g), you can also visualize the repository using the following command (Look for dots without children and without green labels): gitk --all --date-order $(git log -g --pretty=%H)
- Commits or other git data that are no longer reachable through any reference name (branch, tag, etc) are called “dangling” and may be found using fsck. There are legitimate reasons why objects may be dangling through standard actions and normally over 99% of them are entirely uninteresting for this reason.
- Once you git push (or in theory someone pulls from your repo, but people who pull from a working repo often deserve what they get) your changes to the authoritative upstream repository or otherwise make the commits or tags publicly visible, you should ideally consider those commits etched in diamond for all eternity. If you later find out that you messed up, make new commits that fix the problems (possibly by revert, possibly by patching, etc).
- however both reflexive avoidance of branches due to stupidity of other SCM systems and reflexive overuse of branches (since branches are actually easy with git) is most likely ignorance.
- The normal git rule of using the first line to provide a short (50-72 character) summary of the change is also very good. Looking at the output of gitk or git log --oneline might help you understand why.
- You should also enforce your standards on commit messages, when possible, through hooks.
- I’m here to tell you that integrating your bug tracking system with git makes the two systems one thousand times more effective. Specifically, come up with a standard for tagging commits with bug numbers (eg. “Bug 1234: Adjust the frobnoz down by .5”) and then have a receive hook on the upstream repo that automatically appends that commit information to the ticket.
- Copy/move a file in a different commit from any changes to it
- (Almost) Always name your stashes
- Protect your bare/server repos against history rewriting
