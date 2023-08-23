### This  is   All   About Models

1. [Base model](https://github.com/rajibbinalam/Laravel_Doc/blob/master/laravel%20My%20Doc/Base%20Model.md)
2. We can add a service in model:
```php
public function usd_price(){
  return (new CurrencyConverter)->convert($this->price, 'usd', 'eur');
}
```
=> here ```$this->price``` will contain current price attribute(db field)
