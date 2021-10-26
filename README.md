# ArchApt
ArchApt apt to pacman syntax adapter

Usage: `apt [options] command`

ArchApt is a commandline syntax adapter for pacman package manager
used in Arch-based systems that provides a familiar apt syntax for users
used to Debian-based system's apt package manager.

Commands currently supported:
* `list` - list packages based on package names
* `search` - search in package descriptions
* `show` - show package details
* `install` - install packages
* `reinstall` - reinstall packages
* `remove` - remove packages
* `autoremove` - Remove automatically all unused packages (untested!)
* `update` - update list of available packages
* `upgrade` - upgrade the system by installing/upgrading packages
* `full-upgrade` - upgrade the system by removing/installing/upgrading packages

Switches currently supported:
* `--installed` - used with `list` to show a list of currently installed packages
* `--upgradeable` - used with `list` to show a list of packages ready to be upgraded
* `--purge` - used with `remove`, cleans up all additional stuff a packages leaves behind
* `--dry-run` - shows the command actually being issued to pacman, doesn't actually run
* `--yes` or `-y` - does everything without asking for confirmation
* `--fpacman` - force the use of pacman even if yay is installed
* `--fyay` - force the use of yay even if it is not found (don't use, debug purposes only)

When used with `yay` (detects it's presence automatically) it accounts for the habit
of running apt as sudo, which is discouraged by yay due to makepkg security concerns,
but running it as a normal user regardless (provided `runuser` is available).

# Disclaimer
This script was made and is being maintained **for my personal usage only**, it's raw, it doesn't follow best practice guidelines, it doesn't suit someone's ideals of code beauty, and it might very well be **unsafe** to use.  
If it breaks your system, damages your data, leaves your poor cat hungry, e.t.c, you're on your own.   
**If you do make use of it, you're doing this ON YOUR OWN RISK only**. See LICENSE for all the details.   
And, yes, whenever you do find the time for that, you definitely should learn to use pacman. It's great.   
That said, it this script was still of use to you, it makes me happy.

# Installation
## Prerequisites
In order to run this script safely it's **HIGHLY** discouraged to install in into your root bin directory. It is UNSAFE, DON'T DO THIS.  
Instead, if you already can execute scripts from your `/home/USERNAME/bin` folder, put it there. (Feel free to use /home/USERNAME/.local/bin/ if you so prefer).  
If not, read on:
1. Add `export PATH="$HOME/bin:$PATH"` to your `~/.bashrc` file located in your home directory if it's not already there.
2. Run `export PATH="$HOME/bin:$PATH"` in terminal. This will allow you to run scripts from your `~/bin` folder.
3. Run `mkdir -p ~/bin` in terminal to create this folder if it doesn't exist.

## Download, copy and make executable
Run the following in the terminal (*assuming you did the steps above*):
```
git clone https://github.com/RoyShapiro/ArchApt.git
mkdir -p ~/bin
cp ./ArchApt/apt ~/bin/apt
chmod +x ~/bin/apt
```
You can now delete the cloned repo folder if you so wish.  
Installation complete, you can now use apt basically as you would on Debian-based distro.
With the obvious caveat of limited functionality currently provided by this script.

# Usage with yay
If you have `yay` installed, this script will make use of it automatically. Nothing needs to be done.
In order to run with yay, the user issuing the command must *not* be root. It's okay to use sudo, this script should handle this case (provided `runuser` is available, but it should be). If user is root, pacman will be used as backend instead.
