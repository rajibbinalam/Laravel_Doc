## Select2 with Ajax Live Search
### System 1 : Search in one selection Field
#### Html (Blade) setup
```blade
<div class="col-lg-5">
    <div class="input-group mb-2 width-100">
        <span class="input-group-addon width-30" style="text-align: left">
            Customer
        </span>
        <select name="customer_id" class="form-control get-customers-ajax" onchange="getInvoices(this)" style="width: 100%">
            <option value="" selected>- Select -/option>
            @if (request('customer_id'))
            <option value="{{ request('customer_id') }}" selected>{{ request('custo_info') }}</option>
            @endif
            @foreach ($customers as $customer)
            <option value="{{ $customer->id }}" {{ old('customer_id', request('customer_id')) == $customer->id ? 'selected' : '' }}
                  data-customer-invoices="{{ $customer->sales }}" >
              {{ $customer->name }} &mdash; {{ $customer->phone }}
            </option>
            @endforeach
        </select>
    </div>
</div>
```
#### Ajax Setup

```blade
<script src="{{ asset('assets/js/jquery-2.1.4.min.js') }}"></script>
<script src="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/js/select2.min.js"></script>

<script>
    $(document).ready(function() {
        $(".get-customers-ajax").select2({
            ajax: {
                url: "{{ route('pos_erp.sale-return-exchanges.create') }}",
                type: "GET",
                dataType: 'json',
                delay: 250,
                data: function(params) {
                    return {
                        is_ajax: true,
                        search: params.term
                    };
                },
                processResults: function(response) {
                    var options = [];
                    $.map(response, function (item) {
                        let sales = JSON.stringify(item.sales);
                        var option = {
                            text: item.name + ' -- ' + item.phone,
                            id: item.id,
                            sales: sales
                        }
                        options.push(option);
                    })
                    return { results: options };
                },
                cache: false
            },
            templateSelection: function (data, container) {
                $(data.element).attr('data-customer-invoices', data.sales);
                return data.text;
            }
        });

    });

</script>

```

```php
if($request->is_ajax){
    return Customer::with('sales:id,branch_id,customer_id,invoice_no')
                    ->where('name', 'LIKE', '%'.$request->search.'%')
                    ->orWhere('phone', 'LIKE', '%'.$request->search.'%')
                    ->take(50)
                    ->get(['id', 'name', 'phone']);
}
```

### System 2 : Search Two way (left->right & right->left)
##### NB: if search upazila, than `district`, `division`, `country` will auto complete with the relation.
### Reference: Project::SalesForce->Market Setup
