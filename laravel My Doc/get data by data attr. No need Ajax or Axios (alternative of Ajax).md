### In A Relation we can get data by data attribute, no need to use Ajax or Axios
__Controller: Get Suppliers data (Suppliers with purchase relation)__
  
```php
  $data['suppliers']= Supplier::dokani()->with('purchases:id,supplier_id,invoice_no')->get(['id','name','mobile']);
```

__Blade: Suplliers Dropdown Select__

```html,php
<div class="input-group mb-2 width-100">
    <span class="input-group-addon width-30" style="text-align: left">
        Supplier <sup style="color: red">*</sup>
    </span>
    <select name="supplier_id" class="form-control select2" onchange="getInvoices(this)"
        style="width: 100%">
        <option value="" selected>- Select -</option>
        @foreach ($suppliers as $supplier)
        <option value="{{ $supplier->id }}"
            {{ old('supplier_id', request('supplier_id')) == $supplier->id ? 'selected' : '' }}
            data-customer-invoices="{{ $supplier->purchases }}" data-customer-references="{{ $supplier->purchases }}">
            {{ $supplier->name }} &mdash; {{ $supplier->mobile }}
        </option>
        @endforeach
    </select>
</div>
```

__Jquery: To get data supplier wise Purchase invoice__

```javascript
function getInvoices(obj) {

    let invoices = $(obj).find('option:selected').data('customer-invoices');
    // console.log(invoices)
    $(obj).closest('#saleProductExchangeSearchForm').find('#invoice_no').empty();
    $(obj).closest('#saleProductExchangeSearchForm').find('#invoice_no').append(
        `<option value="" selected>- Select -</option>`);

    $(invoices).each(function (index, invoice) {
        $(obj).closest('#saleProductExchangeSearchForm').find('#invoice_no').append(
            `<option value="${ invoice.invoice_no }">${ invoice.invoice_no }</option>`);
    })

}
```
