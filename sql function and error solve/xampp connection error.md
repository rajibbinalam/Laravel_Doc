
__go to :- phpMyAdmin > config.inc.php__

```php
/* Authentication type and info */
$cfg['Servers'][$i]['auth_type'] = 'config';
$cfg['Servers'][$i]['user'] = 'root';
$cfg['Servers'][$i]['password'] = '';
$cfg['Servers'][$i]['extension'] = 'mysqli';
$cfg['Servers'][$i]['AllowNoPassword'] = true;
$cfg['Servers'][$i]['port'] = 3307;           //Added thia line if you change port
$cfg['Lang'] = '';

```

### Error: MySQL shutdown unexpectedly

1. First of all, Close the XAMPP web server completely.
2. Once you have closed the web server, navigate to the folder where xampp is installed. By default, you will find xampp at “C:\xampp”.
3. Inside the xampp folder, open up the mysql folder
4. Now, in the mysql folder, locate the data folder and rename it to data_old.
5. Once you have done that, right-click and from the drop-down menu, create a new folder by going to New > Folder in the mysql directory. Name this newly created folder data.
6. After creating the data folder, go ahead and open up the backup folder. Copy the contents of the backup folder and paste them inside the newly created data folder.
7. Once you have done that, head back to the data_old folder and copy your database folders from there to the new data folder
 ### Note: Skip the mysql, performance_schema and phymyadmin folders from the data_old folder.
 
8. After you have done that, copy the ibdata1 file from the data_old folder and replace it with the one inside the new data folder.
9. Now that you have done all of that, go ahead and run XAMPP as an administrator. Once the XAMPP Control Panel is open, try starting the MySQL server to see if the problem still exists.


 [Open a blog](https://appuals.com/error-mysql-shutdown-unexpectedly/)
