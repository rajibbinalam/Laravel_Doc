## Select2 and chosen select update after JS change or show or added new select option input

### Select2
```php
$('#mySelect2').val(null).trigger('change');
```

### Chosen Select
```php
$("#district_id").val('').trigger("chosen:updated");  # '' or null
```
