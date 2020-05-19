# Apache Web Server

## Start, stop, restart
```bash
service httpd start
service httpd stop 
service httpd restart 
```

## Mininal HTTP configuration
```bash
Listen 0.0.0.0:80
User apache
Group apache
ServerName www.example.com
ErrorLog /var/log/httpd/error.log
LoadModule authz_host_module modules/mod_authz_host.so
LoadModule dir_module modules/mod_dir.so
DirectoryIndex index.html
DocumentRoot /var/www/html
<Directory /var/www/html>
    AllowOverride none
    Order allow,deny
    allow from 192.168.0.0/24
</Directory>
```

## Load modules
```bash
Include conf.d/modules.conf
ExtendedStatus On
<Location /server-status>
    Sethandler server-status
    order allow,deny
    allow from 192.168.0.200
</Location>
<Location /server-info>
    Sethandler server-info
    order allow,deny
    allow from 192.168.0.200
</Location>
```
*/etc/httpd/conf.d/modules.conf*
```bash
LoadModule authz_host_module modules/mod_authz_host.so
LoadModule dir_module modules/mod_dir.so
LoadModule info_module modules/mod_info.so
LoadModule status_module modules/mod_status.so
```

### Check configuration
```bash
apachectl configtest
service httpd restart
```

## Executing CGI scripts
```bash
ScriptAlias /cgi-bin/ /var/www/cgi-bin/
AddHandler cgi-script .cgi
# AddHandler cgi-script .pl
TypesConfig /etc/mime-types
<Directory /var/www/cgi-bin>
    Options +ExecCGI
</Directory>
```
