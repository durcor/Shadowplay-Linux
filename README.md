# Shadowplay On Linux

Shadowplay's replay feature on Linux

- compatible with nvenc (Nvidia), vaapi (AMD), and qsv (Intel), as well as libx264

## Prerequisites

- Have FFMPEG installed
	- `sudo pacman -S ffmpeg`
- Have Xbindkeys installed
	- `sudo pacman -S xbindkeys`
- Have libnotify installed
   - `sudo pacman -S libnotify`

## Installation

Download this repository and run the `install` file.
This will install the required dependencies on Arch and install the systemd user service.

## Configuration

Variables specific to your desired setup can be found in the example_config which is installed to `$HOME/.config/shadowplay`

## Setup

### Keybind Setup
First, configure the key (or key combo) you want to use in order to save your replays.
- For instructions on how to bind keys, check [here](http://xahlee.info/linux/linux_xbindkeys_tutorial.html) 
- Consider making another bind for killing ShadowPlay. (See below)
- Bind a key to the command `killall --user $USER --ignore-case --signal SIGTERM  ffmpeg` so it looks something like this:
```
# make F9 save Shadowplay replay
"killall --user $USER --ignore-case --signal SIGTERM ffmpeg"
   F9

# make F10 kill Shadowplay
"killall -s1 ffmpeg"
   F10
```
- Start xbindkeys with `xbindkeys -f ~/.xbindkeysrc`, or reload it with `killall -s1 xbindkeys` if it's already running, for the new bind to take effect.

### Script

- Run the Shadowplay script with `./shadowplay` in a terminal
- Press your configured hotkey to save the replay. 

## TODO
- Systemd timer integration
- Automatic deletion of video recorded older than the replay buffer
- More flexible audio input support
- Ability to downscale video output during recording

## Notes
When recording for long intervals, it may take some time to save your replays.

Heavily inspired by [Toqozz's script](https://github.com/Toqozz/shadowplay-linux).

Thank you [Tyler](https://github.com/durcor) for answering my stupid questions while making this.
