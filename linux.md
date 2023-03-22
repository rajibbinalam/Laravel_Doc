#### Change/ swetch php version on Linux:
```
sudo update-alternatives --config php
sudo update-alternatives --config phar
sudo update-alternatives --config phar.phar
```

#### Rename all file of a Folder By Extention:
```sh
$ ls -1
test1.foo
test2.foo
test3.foo

$ rename 's/\.foo$/.bar/' *.foo   //rename 's/.old$/.new/' *.old

$ ls -1
test1.bar
test2.bar
test3.bar
```
