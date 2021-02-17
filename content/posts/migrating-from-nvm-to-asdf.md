---
title: Migrating from nvm to asdf
date: 2021-02-17T04:58:16.292Z
tags:
  - tools
comments: true
---
I've been using `zsh` with [antigen][4] as the package manager for years. Over time as I add more customizations, I noticed that my shell startup time has become slow. Sometimes, it would take more than 3 seconds to start up.

I read few months (or a year) ago that nvm, a version manager for `nodejs` can cause [this issue][5] so I thought maybe it's the right time I should try [asdf][1].

[asdf][1] is basically just another tool to manage versions. Instead of having to install tools like [rbenv][2] for ruby or [nvm][3] for `nodejs`, you can just use [asdf][1] and install its plugins to manage all the language versions you're using.

Anyway, I'm not going to talk about what's so good about it. For that, you can read the docs yourself. I'm just going to document the steps I took here.

## Removing nvm completely

To remove nvm completely, here are the steps that I did:

```bash
# list out all the nodes version I'm using
$~ nvm ls
# uninstall nodejs
$~ nvm uninstall <NODEJS_VERSION> 
# uninstall nvm with brew (since I install it using Brew)
$~ brew uninstall nvm
# delete related dotfiles and directory
$~ rm -rf ~/.nvm/ ~/.nvmrc
```

## Installing asdf

I installed [asdf][1] using Brew

```bash
# install asdf using Brew
$~ brew install asdf
```

Then I add the following in my `~/.zshrc` file

```
...
# setup asdf
. /usr/local/opt/asdf/asdf.sh
...
```

That completes the [asdf][1] setup. To install the `nodejs` plugin, I run the following command

```bash
$~ asdf plugin-add nodejs # install nodejs plugin
$~ bash -c '${ASDF_DATA_DIR:=$HOME/.asdf}/plugins/nodejs/bin/import-release-team-keyring # import nodejs release team OpenPGP keys
```

I got an error when trying to import the keys, so I have to install `gpg2` first.

```
$~ brew install gpg2
```

After installing it, I can finally run the `nodejs` installation without any error

```~
$~ asdf install nodejs 15.8.0 # install nodejs version 15.8.0
$~ asdf global nodejs 15.8.0 # set it as the global version
``` 

That's it. I notice that my terminal startup time is a little bit more faster now. I just need to replace [rbenv][2] and [pyenv][6] next

[1]: https://asdf-vm.com/#/
[2]: https://github.com/rbenv/rbenv
[3]: https://github.com/nvm-sh/nvm
[4]: https://github.com/zsh-users/antigen
[5]: https://github.com/nvm-sh/nvm/issues/1277
[6]: https://github.com/pyenv/pyenv