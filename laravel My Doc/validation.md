### Laravel Validation

```php
$request->validate([
    'approval_company'          => 'required',
    'recommender_company'       => 'nullable|same:approval_company',   // It will work only when 'approval_company' are same
    'status'                    => 'nullable|in:all,open,canceled,completed',
    'base_color'                => ['nullable', 'regex:/^[a-f0-9]{6}$/i'],   //  Use RegEx in validation
    'allow_decimal_after_number'=> 'required|integer|gte:1',  // allow decimal after number
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
