## Row (Query Builder) in Laravel
<p>Some time we should use query builder for fetching data faster</p>

#### Getting Transaction with its Payments and select all ```transactions``` fields and add new one for total_paid
```php
$transaction = Transaction::leftJoin('transaction_payments', 'transactions.id', '=', 'transaction_payments.transaction_id')
            ->select('transactions.*')
            ->addSelect(
                DB::raw('(SELECT SUM(IF(TP.is_return = 1,-1*TP.amount,TP.amount)) FROM transaction_payments AS TP WHERE TP.transaction_id=transactions.id) as total_paid'),
            )
            ->where('transactions.id', $assign_detail->transaction_id)->groupBy('transactions.id')->first();

```
