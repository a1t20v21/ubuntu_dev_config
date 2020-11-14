## Install Google Chrome

```
wget -o chrome.deb https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i /tmp/chrome.deb
rm -rf /tmp/chrome.deb
```
## Setup GCC

```
sudo apt install build-essential
```

## Setup required packages

```
sudo apt install vim git curl cmake -y
sudo apt install python3-dev -y
```

## Save git credentials

```
git config --global credential.helper cache
```

## Create git workspace

```
sudo mkdir /opt/workspace
sudo chown -R a1t20v21:a1t20v21 /opt/workspace
ln -s /opt/workspace workspace
cd ~/workspace   
git clone https://github.com/a1t20v21/dotfiles.git
cp ~/workspace/dotfiles/.bash_custom ~/
```

## Add below lines to the end of `.bashrc` file

```
if [ -f ~/.bash_custom ]; then
    . ~/.bash_custom
fi
```
   
## Load terminal configuration

```
dconf load /org/gnome/terminal/ < ~/workspace/dotfiles/gnome_terminal_settings_backup.txt
```   
   
## Configure vim

```
mkdir ~/.vim
cp ~/workspace/dotfiles/.vimrc ~/
mkdir ~/.vim/plugged
mkdir ~/.vim/plugins
cd ~/.vim/plugins/
wget https://raw.githubusercontent.com/joe-skb7/cscope-maps/master/plugin/cscope_maps.vim
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
cd ~/.vim/plugged/youcompleteme/
./install.py 
```

## Setup AMD Radeon Graphics Driver

```
unxz amdgpu-pro-20.40-1147286-ubuntu-20.04.tar.xz 
tar -xvf amdgpu-pro-20.40-1147286-ubuntu-20.04.tar 
cd amdgpu-pro-20.40-1147286-ubuntu-20.04/
sudo ./amdgpu-install 
```

## Setup XP-Pen
```
sudo apt install libqt5xml5
1. Download and install `Linux_Pentablet_V1.2.13.1`
```

## Install Xournal++

## Setup dnsmasq and disable systemd-resolved
`https://kifarunix.com/configure-local-dns-server-using-dnsmasq-on-ubuntu-20-04/`
```
sudo systemctl restart network-manager
sudo netplan apply
```

## Mount google-drive locally
`https://github.com/astrada/google-drive-ocamlfuse`

## Setup rvm
## Setup ruby

## Install Latex/TexStudio
```
sudo apt install texstudio
sudo apt install texlive-latex-extra
sudo apt install texlive-science
```
