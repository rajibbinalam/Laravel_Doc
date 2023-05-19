```php

@php
    $target = new DateTime($trading->end_date);
    $origin = new DateTime(date('Y-m-d'));
    $interval = $origin->diff($target);
@endphp


$interval->days > 0 ? $interval->format('%R%a days Remain')

```
