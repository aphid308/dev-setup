Setup development environment in VirtualBox using Ubuntu Mate 16.10 image from osboxes.org 

Update and Upgrade
sudo apt-get update
sudo apt-get upgrade

Install VirtualBox Guest Additions
sudo apt-get install -y build-essential module-assistant
sudo m-a prepare
Change directory to the GuestAdditions CD image
./VBoxLinuxAdditions.run
follow on screen instructions, reboot. We should have full screen and other features.

Install applications
sudo apt-get install -y git python-pip git vim-gtk cmake python-dev ruby ruby-dev libffi-dev libssl-dev libjpeg-dev virtualenv virtualenvwrapper tmux ipython python3-pip chromium-browser

Clone Configuration Files
git clone https://github.com/aphid308/dotfiles-bootstrap ~/.dotfiles

Create SymLinks for Configuration Files
ln -s ~/dotfiles-bootstrap/.vimrc ~/.vimrc
ln -s ~/dotfiles-bootstrap/.profile ~/.profile
ln -s ~/dotfiles-bootstrap/.bashrc ~/.bashrc
ln -s ~/dotfiles-bootstrap/.tmux.conf ~/.tmux.conf

Install Vundle for Vim Plugin Management
git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim

Install Vim Plugins with Vundle
Launch Vim
vim
Run Command
:PluginInstall

Build Command-T Plugin
cd ~/.vim/bundle/command-t/ruby/command-t
ruby extconf.rb
make

Build YCM Plugin
cd ~/.vim/bundle/YouCompleteMe
./install.py --clang-completer

How to enable Django introspection/YCM completion in Vim with Virtualenv

mkvirtualenv <your django virtualenv>
pip install django
django-admin startproject <project>
cd $VIRTUAL_ENV/bin
vim postactivate
Add:
export DJANGO_SETTINGS_MODULE <project>.settings
deactivate
workon <your django virtualenv>
Test
echo $DJANGO_SETTINGS_MODULE

