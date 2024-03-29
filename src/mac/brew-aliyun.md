# homebrew

## install official
```
/bin/bash -c "$(curl -fsSL https://github.com/Homebrew/install/raw/master/install.sh)"
```

## install aliyun
```
git clone https://mirrors.aliyun.com/homebrew/install.git brew-install
/bin/bash brew-install/install.sh
rm -rf brew-install
```

## show version
```
brew -v
```

## setup aliyun source
```
# temporary config

export HOMEBREW_INSTALL_FROM_API=1
export HOMEBREW_API_DOMAIN="https://mirrors.aliyun.com/homebrew-bottles/api"
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/brew.git"
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/homebrew-core.git"
export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.aliyun.com/homebrew/homebrew-bottles"
brew update
```

```
# permanent config

# zsh user
echo 'export HOMEBREW_API_DOMAIN="https://mirrors.aliyun.com/homebrew-bottles/api"' >> ~/.zshrc
echo 'export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/brew.git"' >> ~/.zshrc
echo 'export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/homebrew-core.git"' >> ~/.zshrc
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.aliyun.com/homebrew/homebrew-bottles"' >> ~/.zshrc
source ~/.zshrc
brew update

# bash user
echo 'export HOMEBREW_API_DOMAIN="https://mirrors.aliyun.com/homebrew-bottles/api"' >> ~/.bash_profile
echo 'export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/brew.git"' >> ~/.bash_profile
echo 'export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/homebrew-core.git"' >> ~/.bash_profile
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.aliyun.com/homebrew/homebrew-bottles"' >> ~/.bash_profile
source ~/.bash_profile
brew update
```

## config tap repository (optional)
```
brew tap -v --custom-remote --force-auto-update homebrew/core https://mirrors.aliyun.com/homebrew/homebrew-core.git
brew tap -v --custom-remote --force-auto-update homebrew/cask https://mirrors.aliyun.com/homebrew/homebrew-cask.git

# other taps
brew tap -v --custom-remote --force-auto-update homebrew/services https://mirrors.aliyun.com/homebrew/homebrew-services.git
brew tap -v --custom-remote --force-auto-update homebrew/cask-fonts https://mirrors.aliyun.com/homebrew/homebrew-cask-fonts.git
brew tap -v --custom-remote --force-auto-update homebrew/cask-versions https://mirrors.aliyun.com/homebrew/homebrew-cask-versions.git
brew tap -v --custom-remote --force-auto-update homebrew/command-not-found https://mirrors.aliyun.com/homebrew/homebrew-command-not-found.git
```

## restore default config
> edit ~/.zshrc or ~/.bash_profile env variable "HOMEBREW" if use permanent config
```
unset HOMEBREW_BREW_GIT_REMOTE
git -C "$(brew --repo)" remote set-url origin https://github.com/Homebrew/brew

unset HOMEBREW_API_DOMAIN
unset HOMEBREW_CORE_GIT_REMOTE
BREW_TAPS="$(BREW_TAPS="$(brew tap 2>/dev/null)"; echo -n "${BREW_TAPS//$'\n'/:}")"
for tap in core cask{,-fonts,-versions} command-not-found services; do
    if [[ ":${BREW_TAPS}:" == *":homebrew/${tap}:"* ]]; then
        brew tap --custom-remote "homebrew/${tap}" "https://github.com/Homebrew/homebrew-${tap}"
    fi
done

brew update
```