### Laravel Validation

```php
$request->validate([
    'approval_company'          => 'required',
    'recommender_company'       => 'nullable|same:approval_company',
    // It will work only when 'approval_company' are same
    'status'                    => 'nullable|in:all,open,canceled,completed'
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
