

__attach()__

Insert related models when working with many-to-many relations
No array parameter is expected
Example:
```php
$user = User::find(1);
$user->roles()->attach(1);
```
__sync()__

Similar to the attach() method, the sync() method is used to attach related models. However, the main differences are:

sync() accepts an array of IDs to place on the pivot table
Secondly, most important, the sync method will delete the data from the pivot table if the model does not exist in the array, and insert only the new items to the pivot table.
Example:

__user_role__
```
id  user_id role_id
1    12       1
2    12       5
3    12       2
```
```php
$user = User::find(12);
$user->roles()->sync(array(1, 2, 3));
```
The above operation will delete:
```
id  user_id role_id
2    12       5
```
And insert role_id 3 to the table.

__user_role table__
```
id  user_id role_id
1    12       1
3    12       2
4    12       3
```

__Real Example: From Medi Lab Project > BlogNews__

After __updateOrCreate__ of Blog:
```php
            $tags = explode(',', $request->tags);
                $tag_id = [];
                foreach ($tags ?? [] as $key => $value) {
                    $tag_id[] = Tag::updateOrCreate([
                        'tag_name' => $value
                    ])->id;
                }
                $modelName->tags()->sync($tag_id ?? []);
```
     OR           
```php
            $tags = explode(',', $request->tags);
                $tag_id = [];
                foreach ($tags ?? [] as $key => $value) {
                    $modelName->tags()->attach($value);
                }
```
