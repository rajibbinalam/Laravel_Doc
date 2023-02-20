```php
$totalAmount = $invoice->stock_adjustment_item->sum(function ($item) {
            return $item->quantity * $item->price;
        });
```
