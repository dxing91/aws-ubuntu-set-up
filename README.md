# aws-ubuntu-set-up

##Create an ubuntu instance on AWS

##First time login
make sure private key file is not publicly viewable
```chmod 400 key.pem```
ssh into server
```ssh -i key.pem username@serveraddress```

##Use root
```sudo -s```

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

## setup reverse proxy 
```
cd /etc/nginx/sites-available/
touch <mysite>
vim mysite
```

write in mysite file

```
server {
    listen 80;

    server_name <mysite>.com;

    location / {
        proxy_pass                  http://APP_PRIVATE_IP_ADDRESS:8080;
        proxy_http_version          1.1;
        gzip                        on;
        gzip_types                  text/css application/javascript text/html;
        gzip_min_length             1000;
        proxy_set_header            Upgrade         $http_upgrade;
        proxy_set_header            Connection      'upgrade';
        proxy_set_header            Host            $host;
        proxy_cache_bypass          $http_upgrade;
    }
}
```

create symlink in sites-enabled
```cd ../sites-enabled```
```ln -s /etc/nginx/sites-available/<mysite> <mysite>```

stop apache server
```/etc/init.d/apache2 stop```

Restart nginx
```sudo service nginx restart```

