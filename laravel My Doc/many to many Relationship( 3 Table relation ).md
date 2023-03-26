#### 1. Table Structure:
```php
structurals
  id
  name

indicators
  id
  name

groupings
 id
 structural_id
 indicator_id

```
#### 2. Model Relationship:
```php
class Indicator extends Model
{
    public function structurals()
    {
        return $this->belongsToMany(Structural::class, 'groupings','structural_id','indicator_id');
    }
}

class Structural extends Model
{
    public function indicators()
    {
        return $this->belongsToMany(Indicator::class, 'groupings'); //'indicator_id','structural_id'
    }
}
```

#### 3. View (Blade File)
```php
use App\Models\Structural;
 
$user = Structural::find(1);
 
foreach ($user->roles as $role) {
    echo $role->pivot->created_at;   //->pivot  == nao takte pare
}
```

#### 4. Searching from __IndicatorController__
```php
Indicator::whereHas('structurals', fn($q) => $q->where('structural_id', $request->structural_id));

```





