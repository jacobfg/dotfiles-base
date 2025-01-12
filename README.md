# Getting base dot file installed for yubikey pgp/ssh

## Install brew & chezmoi

If testing on UTM (via SSH), you need these environment variables

```zsh
export SSH_AUTH_SOCK=$(/bin/ls -d /private/tmp/com.apple.launchd.*/Listeners)
```

```zsh
export PATH=$PATH:/opt/homebrew/bin
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install gnupg pinentry-mac chezmoi
```

## Clone and apply dot files, password store

Due to not being able to order, we need ot run _apply_ twice for gnupg & ssh to setup

```zsh
chezmoi init https://github.com/jacobfg/dotfiles-base.git --apply && chezmoi apply
```

## Remote access on MacOS   

Enable remote access and it's off to the races once you have an IP

```zsh
# sudo systemsetup -setremotelogin on
scutil --nwi | sed -n '/..*IPv4/{n;s/.*: //p;}'
mkdir ~/.gnupg
```
