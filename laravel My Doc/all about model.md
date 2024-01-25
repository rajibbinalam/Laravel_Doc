### #This  is   All   About Models

1. [Base model](https://github.com/rajibbinalam/Laravel_Doc/blob/master/laravel%20My%20Doc/Base%20Model.md)
2. We can add a service in model:
```php
public function usd_price(){
  return (new CurrencyConverter)->convert($this->price, 'usd', 'eur');
}
```
__=> here ```$this->price``` will contain current price attribute(db field)__

### #Model use as Dependency Injection in Controller  (Code in Model)
#### Controller
```php
class SalarySetupController extends Controller{
    public $salary;
    /*
     * CONSTRUCTOR
    */
    public function __construct(Salary $salary) // Salary Model
    {
        $this->salary = $salary;
    }

    public function store(Request $request){
        try {
            DB::transaction(function () use ($request) {

                $id = $this->salary->storeSalary($request);
                $this->salary->storeBankGross($request, $id);    // Call Fn from Model
                $this->salary->storeCashGross($request, $id);    // Call Fn from Model
            });
        } catch (Exception $e) {
            return redirect()->back()->with('error', $e->getMessage());
        }
        return redirect()->back()->with('message', 'Employee Salary Setup Complete');
    }
}
```
#### Model
```php
class Salary extends Model{
    // Store Salary
    public function storeSalary($request){
        $employee = $this->where('employee_id', $request->employee_id)->latest('id')->first();

        //   This will Change status of all rows of the employee_id
        $this->where('employee_id', $request->employee_id)->update(['status' => '0']);

        //  This Will Create new Data in this Salary Model
        $salaryId = $this->create([
            'gazzate_id'        => $request->gazzate_id,
            'employee_id'       => $request->employee_id,
            'salary_type_id'    => $request->salary_type,
            'effect_from_date'  => $request->effect_from,
            'permanent_date'    => $request->permanent_date,
            'promotion_date'    => $request->effect_from,
            'increment'         => 0,
            'total_gross'       => $request->total_gross,
            'status'            => 1

        ])->id;

        return $salaryId;
    }

    // Store Bank Salary
    public function storeBankGross($request, $id){
        foreach (array_filter($request->bank_gross ?? []) as $key => $bank_gross) {
            BankSalary::create([
                'employee_id'           => $request->employee_id,
                'salary_id'             => $id,
                'basic'                 => $request->bank_basic[$key],
                'house_rent'            => $request->bank_house_rent[$key],
                'conveyance'            => $request->bank_conveyance[$key],
                'medical'               => $request->bank_medical[$key],
                'utility'               => $request->bank_utility[$key] ?? 0,
                'gross'                 => $bank_gross,
                'bank_information_id'   => $request->bank_information_ids[$key]
            ]);
        }
    }


    // Update This Salary 
    public function updateSalary($request, $id){
        $this->where('id', $id)->update([
            'salary_type_id'    => $request->salary_type,
            'effect_from_date'  => $request->effect_from,
            'permanent_date'    => $request->permanent_date,
            'promotion_date'    => $request->effect_from,
            'increment'         => abs($request->previous_total_gross - $request->total_gross),
            'total_gross'       => $request->total_gross,
        ]);
    }
}
```

