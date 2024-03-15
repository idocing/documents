# mac launchpad

## change icon size
```
defaults write com.apple.dock springboard-rows -int 6
defaults write com.apple.dock springboard-columns -int 9
```

## restart dock
```
killall Dock
```

## reset dock
```
defaults write com.apple.dock ResetLaunchPad -bool TRUE
```