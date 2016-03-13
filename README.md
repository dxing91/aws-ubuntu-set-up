# aws-ubuntu-set-up
##make sudo
sudo su
## tunnel into cloud linux 
ssh username@serveraddress
## install nvm
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh | bash
source ~/.nvm/nvm.sh
nvm install v5.8.0
nvm use v5.8.0
## install git
apt-get install git-all
