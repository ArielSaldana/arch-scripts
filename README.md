# Installing arch
1. use gnome-disk-utils to create a bootable disk
2. boot the bootable disk
3. once in, run the command archinstall and go through each line to install arch how you see fit.

# Installing our window manager
For this machine we're going to be using the hyprv3 script created by SolDoesTech/hyprV3
1. git clone https://github.com/SolDoesTech/hyprV3.git
2. cd hyprV3
3. `./set-install`
4. follow the installer instructions

# Getting copy / paste to work 

Install the following packages
wl-clipboard cliphist and wofi

In the hyprland config, most likely found in ~/.config/hypr/hyprland.conf add the following lines
1. exec-once = wl-clipboard-history -t
2. wl-paste cliphist store
3. exec-once = rm "$HOME/.cache/cliphist/db" #delete history on every restart

finally setup a bind
`bind=SUPER,SPACE,exec,cliphist list | wofi --show dmenu -H 600 -W 900  | cliphist decode | wl-copy

# Getting screenshots working 
Install the following libraries `grim slurp` 
Then use the script found in https://raw.githubusercontent.com/Moerliy/dotfiles/master/.config/hypr/scripts/grimblast otherwise try running grim -g "$(slurp)"
Due to a bug with nvidia and xdg-desktop screenshots won't fully work

# Installing NIXOS 



# arch-scripts
Arch Scripts


# Updating yay Packages

`sudo yay -Syu`
include development packages in upgrade
`yay -Syu --devel --timeupdate`
