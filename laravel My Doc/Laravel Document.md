
1. Remove / ignore HTML tags and style ==
```php
                        {{ strip_tags(htmlspecialchars_decode($contact->address)) }}
			
			{!! Str::limit(strip_tags($item->description),80, '') !!}
```
or
```php
	@php
                    echo $contact->address;
                @endphp
```
                

2. Created_at  Time Formate ==
```php
	{{ $blog_post->created_at->format('d-M-Y') }} 
	{{ $blog_post->created_at->format('d-M-Y - h:i A') }}  [ format with AM PM ]

	Carbon\Carbon::parse($experience->start_year)->format('d-M-Y')  ----> [ for 2010-01-14 or String to time convert ]
	{{  date('d M, Y', strtotime($doctor->DOB)) }}		----------------|^

	Comment Time === {{ $blog_post->created_at->diffForHumans() }}   <!-- it'll show: 4 Hours Ago -->
	{{ optional($item->product)->created_at->diff(\Carbon\Carbon::now())->format('%yY, %mM') }}  // 1Year , 4 Months
```


3. Text Limit ( details ) == 
```php
use Illuminate\Support\Str;

$truncated = Str::limit('The quick brown fox jumps over the lazy dog', 20, ' (...)');

$string = Str::of('Perfectly balanced, as all things should be.')->words(3, ' >>>');

```
// The quick brown fox (...)


4. Multi Check box
```html
<div class="form-group col-md-6">
    <label><strong>Size :</strong></label><br>
    <label><input style="margin: 6px;" type="checkbox" name="size[]" value="M"> M</label>
    <label><input style="margin: 6px;" type="checkbox" name="size[]" value="S"> S</label>
    <label><input style="margin: 6px;" type="checkbox" name="size[]" value="L"> L</label>
    <label><input style="margin: 6px;" type="checkbox" name="size[]" value="XL"> XL</label>
    <label><input style="margin: 6px;" type="checkbox" name="size[]" value="XXL"> XXL</label>
    <label><input style="margin: 6px;" type="checkbox" name="size[]" value="XXXL"> XXXL</label>
    <label><input style="margin: 6px;" type="checkbox" name="size[]" value="4XL"> 4XL</label>
</div>
```
   and Controller:
 ```php
       $product->colors = implode(',',$request->colors);
```

6 Option Disable ==
```html
<select class="js-example-disabled-results">
	<option value="one">First</option>
	<option value="two" disabled="disabled">Second (disabled)</option>
	<option value="three">Third</option>
</select>
```
```php
var $disabledResults = $(".js-example-disabled-results");
$disabledResults.select2();
```




7. Route Multi Parametter :::
```php
Route::get('/expert/{id}/{name}', [FrontendExpertAdviceController::class, 'expertsDetails'])->name('frontend.expertsDetails');
{{ route('frontend.expertsDetails',['id'=>$data->id,'name'=>$data->name]) }}
```



                        
