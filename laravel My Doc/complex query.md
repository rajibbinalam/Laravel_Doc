## Employee -> hasMany ManualOT -> hasMany / hasOne -> ManualOtDetails;
get Employees with calculate the amount from manual_ot_details wherehas manual_ot month is current / specific month and is_salay_shit = 1;

```php

// Employee Model:
public function manual_ot_details(): HasManyThrough
{
    return $this->hasManyThrough(ManualOtDetail::class, ManualOt::class, 'employee_id', 'manual_ot_id', 'id', 'id');
}

// Retrive the all Employee With Amount of Manual OT
return Employee::query()->withCount(['manual_ot_details'=> fn($q)=>$q->whereHas('manual_ot', fn($qq)=> $qq->where('month', $request->month)->where('in_salary_shit', 1))->select(DB::Raw('SUM(ot_amount)'))])
                ->get();
```
