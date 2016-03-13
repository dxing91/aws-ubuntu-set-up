# aws-ubuntu-set-up

##Create an ubuntu instance on AWS

##Add user / use password not pem
change PasswordAuthentication to yes
change PermitRootLogin to yes (for login)
in ```/etc/ssh/sshd_config```
restart your ssh service
```service ssh restart```

## tunnel into cloud linux 
ssh username@serveraddress
## install nvm
Get it!
```wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh | bash```
add below to ```~/.bashrc```, ```~/.profile```, or ```~/.zshrc```
```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm
```
```source ~/.nvm/nvm.sh```
## Install NVM for NodeJS
```nvm install v5.8.0```
```nvm use v5.8.0```
## update apt
```apt-get update```
## install git
```apt-get install git-all```

## chmod your /var/www repo
sudo chmod -R 777 /var/www/

## clone your repo into /var/www
```cd /var/www```
```git clone your-repo```

## install nginx (proxy server)
```
sudo -s
nginx=stable # use nginx=development for latest development version
add-apt-repository ppa:nginx/$nginx
apt-get install nginx
```
