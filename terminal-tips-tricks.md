-  Everything in `src` folder and everything in every folder
```sh
src/**/*
```
-  Показывает 10 крупнейших по размеру каталогов на верхнем уровне с общей загрузкой. Все в мегабайтах.
`du -cms .[^.]*/ */ | sort -rn | head`

-  Показывает все процессы 
`ps ax`

-  Find files by extension
```sh
find $dir -type f -name '*.txt'
```

-  Install `tar.gz`
```sh
sudo tar xzvf archive-name.tar.gz
cd archive-name
./configure
make
sudo make install
```

- Install dotfiles with stow
`stow -t ~/ **`

- Setup debugger for chrome with chromium
`sudo ln -s /usr/bin/chromium /usr/bin/google-chrome`

- Grep usage example
```sh
urxvt --help 2>&1 | grep font
```
`2>` redirects stderr to an (unspecified) file, appending `&1` redirects stderr to stdout

- Install `.deb` package
 
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
