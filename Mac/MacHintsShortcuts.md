# Mac Commands and Shortcuts

## Commands

Edit Text
sudo open -t /etc/hosts
sudo open -a TextEdit /etc/hosts
sudo subl /etc/hosts

ssh-keygen -t rsa

fg ==> set back to foreground
CTL-C kill
CTL-z put current running process in background
jobs -==> to list jobs and choose which one to fg
open .  <== Opens this folder in Finder

## SEARCH

`type <phrase>`
`which [-p] <phrase>`
`locate -b <phrase>`
`locate -b <phrase> | fgrep -w bin`
/System/Library/Frameworks/CoreServices.framework/Versions/A/Frameworks/LaunchServices.framework/Versions/A/Support/lsregister -dump | grep -i "google chrome"

`networkQuality` Will tell you network speed
`df -h` How much free space is left on your mac
`top` get CPU Hoggers
`kill -9 <pid>` Kill a process (can get from top)
`uptime` How long your Mac hasn’t been shut down?
