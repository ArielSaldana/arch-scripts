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

If you're having issues seeing screenshots on an nvidia GPU
1. sudo pacman -S hyprland-nvidia or yay -S hyprland-nvidia

If you're having issues seeing the cursor
1. go to /usr/share/wayland-sessions/hyprland.conf and change `Exec=Hyprland` to `Exec=env WLR_NO_HARDWARE_CURSORS=1 Hyprland`


# Getting copy / paste to work 

Install the following packages
wl-clipboard cliphist and wofi

In the hyprland config, most likely found in ~/.config/hypr/hyprland.conf add the following lines
1. exec-once = wl-clipboard-history -t
2. wl-paste cliphist store
3. exec-once = rm "$HOME/.cache/cliphist/db" #delete history on every restart

finally setup a bind
`bind=SUPER,SPACE,exec,cliphist list | wofi --show dmenu -H 600 -W 900  | cliphist decode | wl-copy`

# Getting screenshots working 
Install the following libraries `grim slurp` 
Then use the script found in https://raw.githubusercontent.com/Moerliy/dotfiles/master/.config/hypr/scripts/grimblast otherwise try running grim -g "$(slurp)"
Due to a bug with nvidia and xdg-desktop screenshots won't fully work

# oh-my-zsh
install zsh 
`sudo pacman -S zsh -Y`
change the default shell to zsh by running `chsh -s %(which zsh)`
follow the rest of the instructions on the ohmyzsh github:
https://github.com/ohmyzsh/ohmyzsh


# Installing NIXOS (Package manager)
https://wiki.archlinux.org/title/Nix



# Arch-scripts
Arch Scripts


# Updating yay Packages

`sudo yay -Syu`
include development packages in upgrade
`yay -Syu --devel --timeupdate`

# Firewall
Although linux desktops don't really require firewall software, I still use uwf just to be sure.
```
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw enable
```

# Virtualization

Install the following packages
`sudo pacman -S qemu qemu-arch-extra virt-manager libvirt`
optimally if you're running windows also install `edk2-ovmf swtpm` as these will allow you to emulate tpm 

# Gaming
Lutris + Wine + Steam

# Packages I Like

tmux 


# TODO:
Add .dotfiles


# INFO
since we're using systemd we can use the following command to boot into uefi mode
systemctl reboot --firmware-setup
