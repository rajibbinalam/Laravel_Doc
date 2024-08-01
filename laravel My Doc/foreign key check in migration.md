### Check Foreign Key in database Migration Table.

### appServiceProvider::boot()
```php
Str::macro('hasForeignKey', function ($table_name, $field_name) {
    $foreign_key_name = $table_name . '_' . $field_name . '_foreign';
    return count(DB::select(
        DB::raw(
            'SHOW KEYS
            FROM ' . $table_name . '
            WHERE Key_name=\'' . $foreign_key_name . '\''
        )
    )) > 0;
});
```

### Use the check, is there foreignkey avaiable or not than can drop or avoid
```php
Schema::table('projects', function (Blueprint $table) {
    Str::hasForeignKey('projects', 'customer_id', function () use($table) {
        $table->dropForeign(['customer_id']);
    });
});
```
