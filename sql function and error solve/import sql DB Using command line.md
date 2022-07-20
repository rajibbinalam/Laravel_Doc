*********Import SQL file to Database using Command Line in Windows********

1. go to That file where your DB file(file.sql) are stying.
2. run ```cmd``` : 

	```mysql -u root(username) -p database_name < file.sql```

__if having this error:__
'mysql' is not recognized as an internal or external command,
operable program or batch file.

__then__ use this in command	(My path start from C:)

	```
	set path=%PATH%;C:\xampp\mysql\bin;
	```

3. If show ```password:``` . Just Hit __Enter__

**** Wait few Minutes/ Seconds to Exicute this code to import sql file to DB Server**
