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
sudo apt install python3-pip -y
sudo apt install gnustep-gui-runtime -y
sudo apt install gedit-plugin-multi-edit -y
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
```
sudo add-apt-repository ppa:apandada1/xournalpp-stable
sudo apt update
sudo apt install xournalpp
```
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
sudo apt install texstudio -y
sudo apt install texlive-latex-extra -y
sudo apt install texlive-science -y
```

## Setup golang
```
wget -c https://dl.google.com/go/go1.14.2.linux-amd64.tar.gz -O - | sudo tar -xz -C /usr/local
echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.bashrc
```

## Setup jq
```
sudo apt  install jq -y
```

## Setup pyenv
```
sudo apt-get install -y make \
	build-essential \
	libssl-dev \
	zlib1g-dev \
	libbz2-dev \
	libreadline-dev \
	libsqlite3-dev \
	wget \
	curl \
	llvm \
	libncurses5-dev \
	libncursesw5-dev \
	xz-utils \
	tk-dev \
	libffi-dev \
	liblzma-dev \
	python-openssl
curl https://pyenv.run | bash
pyenv install -v 3.8.5
```

## Setup linuxbrew
```
git clone https://github.com/Homebrew/brew ~/.linuxbrew/Homebrew
mkdir ~/.linuxbrew/bin
ln -s ~/.linuxbrew/Homebrew/bin/brew ~/.linuxbrew/bin
eval $(~/.linuxbrew/bin/brew shellenv)
```

## Install tfenv and setup terraform
```
brew install tfenv
tfenv install 0.13.5
```

## PDF Management
```
sudo apt install texlive-pstricks
# Remove password
pdftops -upw <password> file.pdf file.ps
ps2pdf file.ps file.pdf
pdftops in.pdf out.ps
# Set password
ps2pdf -sUserPassword=XXXXX -sOwnerPassword=YYYYY out.ps out.pdf
```

## MySQL 5.6 client on Ubuntu 20.04

1. download binary from https://downloads.mysql.com/archives/community/
2. 
```
sudo add-apt-repository universe
sudo apt-get install libncurses5 libncurses5:i386
tar -xzvf mysql-5.6.40-linux-glibc2.12-x86_64.tar.gz 
cd mysql-5.6.40-linux-glibc2.12-x86_64/bin
./mysql -h hostname.rds.amazonaws.com -uadmin -p
```
