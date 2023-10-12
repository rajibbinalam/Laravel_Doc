## Import SQL file to Database using Command Line

## For Windows OS
1. go to That file where your DB file(file.sql) located.
2. run ```cmd``` :

```sh
mysql -u root(username) -p database_name < file.sql
```

__if having this error:__
'mysql' is not recognized as an internal or external command, operable program or batch file.

__then__ use this in command to set path (My path start from C:):

```sh
set path=%PATH%;C:\xampp\mysql\bin;
```

3. If show ```password:``` . Just Hit __Enter__

**** Wait few Minutes/ Seconds to Exicute this code to import sql file to DB Server**

## For Mac OS
```zsh
mysql -u root -p 
```
```zsh
USE DB_NAME
```
```zsh
source path/filw.sql
ex: source /Users/macbookpro/Downloads/hrm_laravel.sql
```

## For Linux OS

