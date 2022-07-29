# Add apt repository debian

This is an edited version of the add-apt-repository program, which allows debian to directly install Personal Package Archives (PPA) like ubuntu

## Why?

Because I was tired of installing these packages manually, So i edited the program to make direct installation possible

## Installation

```bash
sudo apt-get install software-properties-common
git clone https://github.com/Kamishiro-Kalina/add-apt-repository-debian
sudo cp add-apt-repository-debian/add-apt-repository-debian /usr/bin/add-apt-repository-debian
```

## Usage

Just like on ubuntu, you can just type add-apt-repository-debian (ppa package name) to install the packages

Here is an example of installing Ulauncher

```bash
sudo add-apt-repository-debian ppa:agornostal/ulauncher
sudo apt update
sudo apt install ulauncher
```

The default installed version is focal, if you want to switch the installed version, you can use this option

```bash
sudo add-apt-repository-debian ppa:agornostal/ulauncher -c focal
```

You can also edit the file at /etc/apt/sources.list.d/add-apt-repository-debian/config to change the default installed version

You can replace the original command with the following code  
Add the code to .bashrc, or .zshrc if you are using zsh

```hash
add-apt-repository() {
    command add-apt-repository-debian "$@"
}
sudo() {
    if [ "$1" = "add-apt-repository" ]; then
        shift
        command sudo add-apt-repository-debian "$@"
    else
        command sudo "$@"
    fi
}
```

## Important

There is no guarantee that the ppa package is absolutely stable, the ppa package is not designed to be used by Debian

Any version of Ubuntu 21.10 (impish,jammy,kinetic) and above cannot be installed on debian, This is because debian's dpkg does not recognize the tar.zst format
