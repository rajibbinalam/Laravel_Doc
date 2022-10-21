__1. Table Structure:__
```
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
__2. Model Relationship:__
```
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

__3. View (Blade File)__
```
use App\Models\Structural;
 
$user = Structural::find(1);
 
foreach ($user->roles as $role) {
    echo $role->pivot->created_at;   //->pivot  == nao takte pare
}
```