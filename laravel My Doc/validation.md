### Laravel Validation

```php
$request->validate([
    'approval_company'          => 'required',
    'recommender_company'       => 'nullable|same:approval_company',   // It will work only when 'approval_company' are same
    'status'                    => 'nullable|in:all,open,canceled,completed',
    'base_color'                => ['nullable', 'regex:/^[a-f0-9]{6}$/i'],   //  Use RegEx in validation
    'allow_decimal_after_number'=> 'required|integer|gte:1',  // allow decimal after number
],[
    'approval_company.required' => 'Approval Company is required',
    'recommender_company.same' => 'Recomender Company is must same as Approval company',
]);
```

```php
$validator = Validator::make(
    $request->all(),
    [
        'atnd_mode'   => 'required',
    ]
);
if ($validator->fails()) {
    return response()->json([
        'status'    => 0,
        'data'      => 'Error',
        'message'   => $validator->errors()->first(),
    ]);
}
```
```php
// Update($id)
$request->validate([
    'name'  => 'required|unique:couriers,name,'.$id
]);
```
