# setup dots script

# TODO
# Setup install and change shell to zsh
# Move wallpapers into correct place

# install software
## software to install
# i3
# feh
# neovim
# conky
# rofi

# rename directory
mv ../{dotfiles,.config}
cd ..
cd .config/

sudo apt update
sudo apt -y upgrade

# install and change shell to zsh
sudo apt -y install zsh
chsh -s /bin/zsh        # change shell for user and root
sudo chsh -s /bin/zsh

# install slim login manager
sudo apt install slim

sudo apt -y install compton
sudo apt -y install feh

# setup symlinks
ln -s  ~/.config/default-display-manager /etc/X11/default-display-manager
ln -s  ~/.config/conky/sidekick/sidekick.conkyrc ~/.conkyrc
ln -s ~/.config/zshrc ~/.zshrc
ln -s ~/.config/xinitrc ~/.xinitrc
ln -s ~/.config/Xresources ~/.Xresources
ln -s ~/.config/fehbg ~/.fehbg
ln -s ~/.config/vim/ ~/.vim
ln -s ~/.config/vim/vimrc ~/.vimrc
sudo ln -s ~/.config/slim/slim.conf /etc/slim.conf
