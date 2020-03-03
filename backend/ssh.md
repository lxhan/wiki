# SSH Cheat Sheet

# SSH key

1. Generate key `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
2. Start ssh-agent in background `eval "$(ssh-agent -s)"`
3. Add ssh key to ssh-agent `ssh-add ~/.ssh/id_rsa`
4. Copy to clipboard \(linux\) `xclip -sel clip < ~/.ssh/id_rsa.pub`
5. Copy to clipboard \(mac\) `pbcopy < ~/.ssh/id_rsa.pub`


### Login via SSH with password (LOCAL SERVER)
```$ ssh user@192.168.1.29```

### Create folder, file, install Apache (Just messing around)
```$ mkdir test```

```$ cd test```

```$ touch hello.txt```

```$ sudo apt-get install apache2```


### Generate Keys (Local Machine)
```$ ssh-keygen```

### Add Key to server in one command
```> cat ~/.ssh/id_rsa.pub | ssh user@192.168.1.29 "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >>  ~/.ssh/authorized_keys```

### Create & copy a file to the server using SCP
```$ touch test.txt```
```$ scp ~/test.txt user@192.168.1.29:~```


## DIGITAL OCEAN

> Create account->create droplet

### Create Keys For Droplet (id_rsa_do)
```$ ssh-keygen -t rsa```

> Add Key When Creating Droplet

### Try logging in
```$ ssh root@doserver```

### If it doesn't work
```$ ssh-add ~/.ssh/id_rsa_do```
(or whatever name you used)

### Login should now work
```$ ssh root@doserver```

### Update packages
```$ sudo apt update```

```$ sudo apt upgrade```

### Create new user with sudo
```$ adduser user```

```$ id user```

```$ usermod -aG sudo user```

```$ id user```

### Login as user 
```> ssh user@doserver```

### We need to add the key to brads .ssh on the server, log back in as root
```$ ssh root@doserver```

```$ cd /home/user```

```$ mkdir .ssh```

```$ cd .ssh```

```$ touch authorized_keys```

```> sudo nano authorized_keys```
(paste in the id_rsa_do.pub key, exit and log in as brad)

### Disable root password login
```$ sudo nano /etc/ssh/sshd_config```

### Set the following
```PermitRootLogin no```

```PasswordAuthentication no```

### Reload sshd service
```$ sudo systemctl reload sshd```

### Change owner of /home/brad/* to brad
```$ sudo chown -R user:user /home/user```

### May need to set permission
```$ chmod 700 /home/user/.ssh```

### Install Apache and visit ip
``` $ sudo apt install apache2 -y```

## Github

### Generate Github Key(On Server)
``` $ ssh-keygen -t rsa```
(id_rsa_github or whatever you want)

## Add new key
```$ ssh-add /home/brad/.ssh/id_rsa_github```

## If you get a message about auth agent, run this and try again
```$ eval `ssh-agent -s````

## Clone repo
```$ git clone git@github.com:bradtraversy/react_otka_auth.git```

## Install Node
```$ curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -```

```$ sudo apt-get install -y nodejs```

## Install Dependencies
```  $ npm install ```

## Start Dev Server and visit ip:3000
```$ npm start```

## Build Out React App
``` $ npm run build```

## Move static build to web server root
``` $ sudo mv -v /home/user/react_otka_auth/build/* /var/www/html```
