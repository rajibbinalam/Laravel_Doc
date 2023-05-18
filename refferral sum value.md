### Sum Balance From all Child (Deeply Nested) refferral.

#### Relation in Model:
```php
public function child_user(){
  return $this->hasMany(User::class, 'ref_by', 'id')->select('id', 'username', 'ref_by', 'balance')->with('child_user');
}
```

#### Helper Function
```php
<?php

$GLOBALS['balance'] = 0;

function sumTradingDataBalance($user){
# OR we Can use variable for stay(not delete after function end or start) Like this------
#  static $balance = 0;
    foreach ($user->child_user ?? [] as $childUser) {
        $GLOBALS['balance'] += $childUser->balance ?? 0;
        sumTradingDataBalance($childUser);
    }
    return $GLOBALS['balance'];
}
````

#### Controller
```php
$user = User::with('child_user')->select('id', 'username', 'ref_by', 'balance')->find(1);
$sum = sumTradingDataBalance($user);
return [
    'sum' => $sum
];
```
