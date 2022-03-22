## SSH key

### Generate SSH keys
1. Generate key `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
2. Start ssh-agent in background `eval "$(ssh-agent -s)"`
3. Add ssh key to ssh-agent `ssh-add ~/.ssh/id_rsa`
4. Copy to clipboard \(linux\) `xclip -sel clip < ~/.ssh/id_rsa.pub`
5. Copy to clipboard \(mac\) `pbcopy < ~/.ssh/id_rsa.pub`


### Login via SSH with password (LOCAL SERVER)
```ssh user@192.168.1.29```

### Create folder, file, install Apache 
```sh
mkdir test
cd test

touch hello.txt

sudo apt-get install apache2
```

### Login to remote mysql server via ssh tunnel
```sh
ssh -R 3307:server-ip:3307 -i ~/path/to/key user@server-ip
```

### Generate Keys (Local Machine)
```sh
ssh-keygen
```

### Add Key to server in one command
```sh
cat ~/.ssh/id_rsa.pub | ssh user@192.168.1.29 "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >>  ~/.ssh/authorized_keys
```

### Create & copy a file to the server using SCP
```sh
touch test.txt
scp ~/test.txt user@192.168.1.29:~
```


## DIGITAL OCEAN


### Create Keys For Droplet (id_rsa_do)
```sh
ssh-keygen -t rsa
```

### Try logging in
```sh
ssh root@doserver
```

### If it doesn't work
```sh
ssh-add ~/.ssh/id_rsa_do
```

### Login should now work
```sh
ssh root@doserver
```

### Update packages
```sh
sudo apt update
sudo apt upgrade
```

### Create new user with sudo
```sh
adduser user
id user
usermod -aG sudo user
```

### Login as user 
```sh
ssh user@doserver
```

### We need to add the key to .ssh on the server, log back in as root
```sh 
ssh root@doserver
cd /home/user
mkdir .ssh
cd .ssh
vim authorized_keys
# paste in the id_rsa_do.pub key, exit and log in as user 
```

### Disable root password login
```sh
sudo vim /etc/ssh/sshd_config
```

### Set the following
```
PermitRootLogin no
PasswordAuthentication no
```

### Reload sshd service
```sh
sudo systemctl reload sshd
```

### Change owner of /home/user/* 
```sh
sudo chown -R user:user /home/user
```

### May need to set permission
```sh
chmod 700 /home/user/.ssh
```

### Install Apache and visit ip
```sh
sudo apt install apache2 -y
```

## Github

### Generate Github Key(On Server)
```sh
ssh-keygen -t rsa
```

### Add new key
```sh
ssh-add /home/user/.ssh/id_rsa
```

### If you get a message about auth agent, run this and try again
```sh
eval ssh-agent -s
```

### Clone repo
```sh
git clone git@github.com:user/repo.git
```
