### (23000015) make this with user id when id is 15 and year is 2023
```php
 $user_id = sprintf("%06d", $this->user->id); // $this->user->id = 15
return date('y') . $user_id;
```
