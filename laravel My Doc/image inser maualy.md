```

            if($request->hasFile('image')){

                $file    = $request->file('image');
                $ext = $file->getClientOriginalExtension();
                $file_name = 'sister_concern_image' .time() . '.' . $ext;
                $location= '/images/products/';
                $file->move(public_path() . $location, $file_name);
                $imageLocation= $location. $file_name;
                
            }
```
