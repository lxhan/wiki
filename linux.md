# Linux

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
