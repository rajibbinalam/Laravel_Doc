 ### Create Blade::directive in Service provider (appServiceProvider) for direct use somthing in a blade

#### boot()
```php
Blade::directive('noTableRecordsFound', function () {
    return '<tr class="bg-danger">
        <th class="text-center text-danger" style="font-size: 18px;line-height:50px" colspan="30">
            <i class="fa fa-exclamation-triangle"></i> No Data Found
        </th>
    </tr>';
});
```
