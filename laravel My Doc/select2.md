
1. __selec2 cdn__

```
<link href="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/css/select2.min.css" rel="stylesheet" />

<script src="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/js/select2.min.js"></script>
```

2.     
```
<script>
        $(document).ready(function() {
            // Select2 Multiple
            $('.select2-multiple').select2({
                placeholder: "Select",
                allowClear: true
            });

        });

</script>
```

		******----------------  Check----------------  ****

```
<select class="select2-multiple form-control" name="tags[]" multiple="multiple" id="select2Multiple">
       <option value="tag1">tag1</option>
       <option value="tag2">tag2</option>
       <option value="tag3">tag3</option>               
</select>
```


<h4>If use In javascript Like THis</h4>

```
$(document).on("click",".AddEventNewPckgItem", function(){
	var whole_extra_item_add = `<tr  class="remove_able_tr_PckgItem">
					<td>
					    <select name="pckg_facility[]" class="form-control select2" onchange="preventDuplicate(this)">
						<option value="">-Select-</option>
						@foreach ($pckg_facilities as $item)
						<option value="{{ $item->id }}">{{ $item->title }}</option>
						@endforeach
					    </select>
					</td>
					<td><button type="button" class="btn btn-danger btn-sm removeEventPckgItem">-</button></td>
				    </tr>`
	$(".table_body_PckgItem").append(whole_extra_item_add);
	counter++;
	$('.select2').select2()
    });
```

<h4>then you must initialize</h4>

```
$('.select2').select2()
```
