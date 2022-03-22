## Everything in `src` folder and everything in every folder
```sh
src/**/*
```

## Shows 10 biggest directories by size in MB
```sh
du -cms .[^.]*/ */ | sort -rn | head
```

## Shows all processes 
```sh
ps ax
```

## Find files by extension
```sh
find $dir -type f -name '*.txt'
```

## Install `tar.gz`
```sh
sudo tar xzvf archive-name.tar.gz
cd archive-name
./configure
make
sudo make install
```

## Install dotfiles with stow 
```sh
stow -t ~/ *
```

## Setup debugger for chrome with chromium 
```sh
sudo ln -s /usr/bin/chromium /usr/bin/google-chrome
```

## Grep usage example
```sh
urxvt --help 2>&1 | grep font
```

`2>` redirects stderr to an \(unspecified\) file, appending `&1` redirects stderr to stdout


## Install `.deb` package
  1. Depackage
     ```sh
     sudo dpkg -i /path/to/deb/file
     ```

     When dpkg install a package and package dependency is not satisfied, it leaves the package in unconfigured state and that package is considered as broken.

  2. Install
     ```sh
     sudo apt-get install -f
     ```

     `sudo apt-get install -f` command tries to fix this broken package by installing the missing dependency.

## Go back 
```sh
cd -
```

## History arrow down / arrow up alternative 
```sh
ctrl + p
ctrl + n
```

## Move one word left / right 
```sh
alt + b 
alt + f
```

## Delete symbol to the right / left from cursor 
```sh
ctrl + d 
ctrl + h
```

## Cut from cursor to start / end of the line 
```sh
ctrl + u / ctrl + k
```

## Cut word to the left from cursor 
```sh
ctrl + w
```

## Paste from buffer 
```sh
ctrl + y
```

## Watch logs
```sh
tail -f /var/log/httpd/access_log.2020-03-0*
```

## List all local users
```sh
cut -d: -f1 /etc/passwd
```

## Check if something running on specific port

```sh
apt install net-tools

netstat -plant | grep 443

lsof -i :80
```

## CPU info 

```sh
nproc

lscpu
```

## Get and set user limits

```sh
ulimit -n
```

## Benchmark server

```sh
sudo apt install apache2-utils -y

ab -n 100 -c 10 http://ip-address/
```
