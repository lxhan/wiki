# Linux

[Linux Productivity Tools](https://www.usenix.org/sites/default/files/conference/protected-files/lisa19_maheshwari.pdf)

## Input / output
`0 = STDIN`
`1 = STDOUT`
`2 = STDERR`

### Write to standard output
```sh
cat > output.txt
cat 1> output.txt
```

### Append to standard output
```sh
cat >> output.txt
```

### Redirection
_Redirection of STDOUT breaks pipelines_
```sh
cat -k asdf 2> error.txt
cat -k asdf 2>> error.txt
```

### Read file and redirect to output
```sh
cat 0< index.html 1> index.php
cat < index.html > index.php
```

### Piping output
_Piping connects STDOUT of one command to the STDIN of another_
```sh
date | cut -d " " -f 1
date | cut -d " " -f 2 > ~/month.txt
```

### Tee
_To save a data 'snapshot' without breaking pipelines_
```sh
date | tee ~/date.txt | cut -d " " -f 1 > today.txt
```

### Xargs
_To pipe if command does not accept STDIN_
```sh
date | cut -d " " -f 1 | xargs echo
cat files_to_delete.txt | xargs rm
```

## File system

| Directory   | Purpose                                                                   |
| ---         | ---                                                                       |
| **/     **  | Root                                                                      |
| **/bin  **  | Common user command binaries _ex. date, cat, cal_                         |
| **/boot **  | Bootable linux kernel and bootloader config files                         |
| **/dev  **  | Devices _ex. tty=terminal, sd or hd = hard disks, ram etc._               |
| **/home **  | Home directories for regular users                                        |
| **/media ** | Removable media mounting directory _ex. usb_                              |
| **/lib  **  | Libraries needed by applications in `/bin` and `/sbin` to boot the system |
| **/mnt  **  | External devices mounting directory (supressed by `/media`)               |
| **/misc **  | Used to sometimes automout filesystems on request                         |
| **/opt  **  | Directory structure used to store additional software                     |
| **/proc **  | Information about system resources                                        |
| **/root **  | Home folder for the root user                                             |
| **/sbin **  | Administrative command binaries for super user                            |
| **/tmp  **  | Temporary files used by running apps                                      |
| **/usr  **  | Users files that don't change after installation                          |
| **/var  **  | Variable data _ex. logs_                                                  |
| **/etc  **  | Administrative config files                                               |

### Creating files with brace expansion
```sh
mkdir {jan, feb, mar, apr, may, jun, jul, aug, sep, oct, nov, dec}_{2020, 2021}
touch file_{a..z}_{0..9}.txt
```

## Wildcards

- `*` matches anything
- `?` matches anything but just for one place
- `[]` matches just one place but allow to specify regular expression

```sh
ls file*.txt
ls file?.txt
ls file[0-9].txt
```
