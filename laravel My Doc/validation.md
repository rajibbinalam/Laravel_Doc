### Laravel Validation

```php
$request->validate([
    'approval_company'          => 'required',
    'recommender_company'       => 'nullable|same:approval_company', 
    // It will work only when 'approval_company' are same
]);
```
