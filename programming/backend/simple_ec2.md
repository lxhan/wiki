# Simple EC2

### Web server setting
1. Update: `yum update -y`
2. PHP check: `php -v`
3. Apache check: `httpd -v`
4. Install php, apache, mysql: `yum install -y httpd24 php73 mysql57-server php73-mysqlnd`
5. Start Apache: `service httpd start`
6. Enable apache on system boot: `chkconfig httpd on`
7. Check if apache is running: `chkconfig --list httpd`. Should be ON in runlevels `2, 3, 4, 5`

### User and permissions
1. Add user: `useradd name`
2. Create directory: `mkdir .ssh html`
3. Copy auth keys: `cp /home/ec2-user/.ssh/authorized_keys /home/loveto/.ssh`
4. Change owner: `chown -R name:name .ssh html`
5. Change permissions: `chmod +x /home/name`

### Edit apache configuration

`vi /etc/httpd/conf/httpd.conf`

```sh
DocumentRoot "/home/loveto/cms"
<Directory />
    AllowOverride none
    <LimitExcept GET POST>
        Order allow,deny
        Deny from all
    </LimitExcept>
</Directory>

<Directory "/home/loveto/cms">
    AllowOverride none
    <LimitExcept GET POST>
        Order allow,deny
        Deny from all
    </LimitExcept>
</Directory>

<IfModule log_config_module>
    # Add for custom logs
    CustomLog "|/usr/sbin/rotatelogs /var/log/httpd/access_log.%Y-%m-%d 86400 +540" common
    CustomLog "logs/access_log" combined
</IfModule>
```

## Git

`yum install git`

### Create empty git repo
```sh
cd /home/loveto
mkdir cms && cd cms
mkdir cms.git && cd cms.git
git init --bare
```

### Setup git hooks
```sh
cd hooks
vim post-receive

#!bin/bash
git --work-tree=/home/user/html --git-dir=/home/user/html/html.git checkout -f

chmod +x post-receive
```

### On your local computer
```sh
mkdir project-name && cd project-name 
git init
```

### Add server remote
```sh
git remote add production ssh://user@ip/home/user/html/html.git

# pull
git pull production master

# push
git push production master
```

### Example
```sh
git add .
git commit -m "commit message"
git push bitbucket master
git push production master

# may help with some errors 
git pull bitbucket master --rebase
git pull production master --rebase
```
