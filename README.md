# Welcome to my dotfiles

This is a new repository for my old dotfiles.
I used to move all my dotfiles into a subdirectory of $HOME (called `dot`)
and symlink the files in there back to $HOME.
This allowed me to initialize a git repository in `$HOME/dot`,
giving me the power of version control for my dotfiles,
while also allowing me to back them up and share them with you.

However,
new setups became a hassle,
so I wrote a bash script,
that would back up existing files,
and link my dotfiles to home.

But with a growing repository,
with changes in Linux (migration from dotfiles to .config)
and growing number of machines under my control,
as well as growing number of dotfiles I created,
this has become more and more of an hassle.
So, [nearly 10 years later](https://github.com/pygospa/dotfiles_old/commit/27128e73534a8772898fa595dd2d1eeb179b256b)
I've decided to finally address this with a new repository,
following the setup presented at [hacker news](https://news.ycombinator.com/item?id=11071754) a while ago.

## Initial setup

```
git init --bare $HOME/.dotfiles
alias dotfiles='/usr/bin/git --git-dir=$HOME/.dot/ --work-tree=$HOME'
dotfiles config --local status.showUntrackedFiles no
echo "alias dotfiles='/usr/bin/git --git-dir=$HOME/.dot/ --work-tree=$HOME'" >> $HOME/.zshrc
dotfiles remote add origin git@github.com:pygospa/dotfiles.git
```

## Cloning dotfiles into a new machine

```
git clone --separate-git-dir=$HOME/.dotfiles git@github.com:pygospa/dotfiles.git $HOME/dotfiles-tmp
cp ~/dotfiles-tmp/.gitmodules ~
rm -rf ~/dotfiles-tmp/
alias dotfiles='/usr/bin/git --git-dir=$HOME/.dot/ --work-tree=$HOME'
```

## Using my dotfiles

I don't believe that anyone would simply check out my entire dotfiles folder
to use it, so for you this shouldn't be a loss.
Instead you probably pick out the bits and pieces you find useful
and copy them to your files.
GitHub also allows to download single files or directories,
if you do want to use an entire config.
Feel free.
