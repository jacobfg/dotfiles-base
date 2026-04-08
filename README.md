# Getting base dot file installed for yubikey pgp/ssh

## Install brew & chezmoi

If testing on UTM (via SSH), you need SSH_AUTH_SOCK, pass via SSH config

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

Set SSH config if not set via SSH config

```zsh
export SSH_AUTH_SOCK=$(~/.gnupg/S.gpg-agent.ssh)
```
