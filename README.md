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
```source ~/.nvm/nvm.sh```
## Install NVM for NodeJS
```nvm install v5.8.0```
```nvm use v5.8.0```
## install git
```apt-get install git-all```
