---
title: "Set Default Git Push Behaviour"
date: 2018-08-22T18:44:01+08:00
draft: false
---

I tend to forget that I have to specify the current branch name when pushing it to a remote.
For example:

```
$~ git push
```

or like this

```
$~ git push -u origin
```

Either way, these commands tend to fail when I haven't yet set the upstream branch. 
`git` will return an error similar like this:

```
fatal: The current branch develop has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin <INSERT BRANCH NAME HERE>
```

To avoid this, I have to set the upstream branch name explicitly first before pushing it
to the remote repository. For example:

```
$~ git push -u origin <INSERT BRANCH NAME HERE>
```

However, this approach can get pretty tedious since the name of my branches are usually long and usually prefixes with
`feature/`, `chore/` or `fix/`. I can't exactly depend on tab-completion either since I have to tab multiple times before pushing in the branch that I wanted to.

Good thing there is a way for me to implicitly push the current branch by configuring the default git behaviour.
Regardless if the branch already exists in upstream or not. Neat right? To do this simply run the following in your terminal:

```
$~ git config --global push.default current
```

`git` will then implicitly assume that I want to push my current branch to upstream. With the configuration set up, I can now simply push my current branch to upstream with the simple command of:

```
$~ git push
```

That's really short and simple. Pretty neat right?

---

<small>
Disclaimer: It's probably not a good practice but I like it since it fits my current git workflow. If I want to avoid using Git GUI tools, I definitely need to reduce the learning curve by making it simpler and easier than the tools that I'm used too.
</small>