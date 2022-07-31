Make a Traids for it and use the Traids name in model

__1. auto update or create created_by & updated_by when creating and updating this model Data__

```
public static function boot()
    {
        parent::boot();

        if (!App::runningInConsole()) {
            /**
             * Auto create created_by field when create anything through model
             */
            static::creating(function ($model) {
                $model->fill([
                    'created_by' => auth()->id() ?? 1,
                    'updated_by' => auth()->id() ?? 1
                ]);
            });

            /**
             * Auto update updated_by field when update anything of the model data
             */
            static::updating(function ($model) {
                $model->fill([
                    'updated_by' => auth()->id() ?? 1
                ]);
            });
        }
    }
    
```

__2. autometicly update or create Monthly Report when create or update any data of Transactions Table__ (See..  Cable Billing => TransactionEventTracker )

```
   public static function boot()
    {
        parent::boot();

        if (!App::runningInConsole()) {
            // $month = request()->method() != 'POST' ? request('month') : date('m');
            $month = request('month') ?? date('m');
            $year = request('year') ?? date('Y');

            /**
             * Auto create created_by field when create anything through model
             */
            static::created(function ($model) use($month, $year) {
                if (is_array($month)) {
                    $month = $model->bill_month;
                }
                if (is_array($year)) {
                    $year = $model->bill_year;
                }
                (new CustomerTransactionService())->storeOrUpdate($model->customer_id, $year, $month);
            });

            /**
             * Auto update updated_by field when update anything of the model data
             */
            static::updated(function ($model) use($month, $year) {
                if (is_array($month)) {
                    $month = $model->bill_month;
                }
                if (is_array($year)) {
                    $year = $model->bill_year;
                }
                (new CustomerTransactionService())->storeOrUpdate($model->customer_id, $year, $month);
            });
        }
    }
    
```
