# Terminal tips & tricks

## Everything in `src` folder and everything in every folder

```bash
src/**/*
```

## Показывает 10 крупнейших по размеру каталогов на верхнем уровне с общей загрузкой. Все в мегабайтах. 
```bash
du -cms .[^.]*/ */ | sort -rn | head
```

## Показывает все процессы 
```bash
ps ax
```

## Find files by extension
```bash
find $dir -type f -name '*.txt'
```

## Install `tar.gz`
```bash
sudo tar xzvf archive-name.tar.gz
cd archive-name
./configure
make
sudo make install
```

## Install dotfiles with stow 
```bash
stow -t ~/ *
```

## Setup debugger for chrome with chromium 
```bash
sudo ln -s /usr/bin/chromium /usr/bin/google-chrome
```

## Grep usage example
```bash
urxvt --help 2>&1 | grep font
```

`2>` redirects stderr to an \(unspecified\) file, appending `&1` redirects stderr to stdout


## Install `.deb` package
  1. Depackage

     ```bash
     sudo dpkg -i /path/to/deb/file
     ```

     When dpkg install a package and package dependency is not satisfied, it leaves the package in unconfigured state and that package is considered as broken.

  2. Install

     ```bash
     sudo apt-get install -f
     ```

     `sudo apt-get install -f` command tries to fix this broken package by installing the missing dependency.

## Go back 
```bash
cd -
```

## History arrow down / arrow up alternative 
```bash
ctrl + p
ctrl + n
```

## Move one word left / right 
```bash
alt + b 
alt + f
```

## Delete symbol to the right / left from cursor 
```bash
ctrl + d 
ctrl + h
```

## Cut from cursor to start / end of the line 
```bash
ctrl + u / ctrl + k
```

## Cut word to the left from cursor 
```bash
ctrl + w
```

## Paste from buffer 
```bash
ctrl + y
```

