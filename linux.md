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
- Redirection of STDOUT breaks pipelines
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
- Piping connects STDOUT of one command to the STDIN of another
```sh
date | cut -d " " -f 1
date | cut -d " " -f 2 > ~/month.txt
```

### Tee
- To save a data 'snapshot' without breaking pipelines
```sh
date | tee ~/date.txt | cut -d " " -f 1 > today.txt
```

### Xargs
- To pipe if command does not accept STDIN
```sh
date | cut -d " " -f 1 | xargs echo
cat files_to_delete.txt | xargs rm
```
