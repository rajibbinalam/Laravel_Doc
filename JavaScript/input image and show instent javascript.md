### Javascript Code
```Javascript
var loadFile = function (event) {
    var reader = new FileReader();
    reader.onload = function () {
        var output = document.getElementById('photoPreview');
        output.src = reader.result;
    };
    reader.readAsDataURL(event.target.files[0]);
};
```



### HTML Code
```html
   <div class="form-group col-md-6">
        <label class="col-sm-3 control-label text-right logo-text"> Organization Logo<span
                class="text-danger">*</span> </label>
        <div class="col-sm-9">
            <img class="company-logo" src="{{ asset($company->logo) }}" width="140" height="120"
                id="photoPreview">
            <input type="file" name="favicon" class="form-control" accept="image/*" onchange="loadFile(event)">
            @error('favicon')
                <small class="text-danger">{{ $message }}</small>
            @enderror
        </div>
    </div>
 ```
 
### Another Jquery Plugin
[https://www.jqueryscript.net/form/ajax-file-uploader.html](https://www.jqueryscript.net/form/ajax-file-uploader.html)
