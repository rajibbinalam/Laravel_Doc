__Approach 1. Exact URL__
```
<li class="{{ (request()->is('admin/cities')) ? 'active' : '' }}">  
```

__Approach 2. Starting with the URL__
```
<li class="{{ (request()->is('admin/cities*')) ? 'active' : '' }}">  
```

__Approach 3. Matching Route__
```
<li class="{{ Route::is('customer.create') ? 'active' : '' }}"> 



__Approach 4. Matching URL Segment__
```
<li class="{{ (request()->segment(2) == 'cities') ? 'active' : '' }}">  
```
