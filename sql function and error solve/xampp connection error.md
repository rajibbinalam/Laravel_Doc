
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
