# Useful Unix commands

## Ubuntu
``` properties
sudo apt

sudo apt-get

```

## Others

### Compile c code into exe format
`gcc ex1.c -o ex1.exe`

### Pass text in test1.in into ex1.exe
`./ex1.exe < test1.in`

`./ex1.exe < test1.in > myOut1.txt`

### Comparing files
`diff test1.out myOut1.txt`

### Unzip the zip files
`gunzip -c lab1.tar.gz | tar xvf -`

### Remove whole folder (-r recusrive)
`yes | rm -r folder` // for sunfire since it keeps asking confirmation

`rm -r folder` // for xcne

### Unzip all .zip files in a folder and put them into separate folders
`find . -name '*.zip' -exec sh -c 'unzip -d "${1%.*}" "$1"' _ {} \;`

## SSH
### Move **files** from local storage to remote location, e.g. sunfire
`scp lab1.tar.gz yuchun@sunfire.comp.nus.edu.sg:lab1.tar.gz`

### Move **folder** from sunfire to xcne5, -r
`scp -r lab1.tar.gz yuchun@xcne5:lab1.tar.gz`
