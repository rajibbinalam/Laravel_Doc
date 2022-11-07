__searchByField__  // __SearchByDateFrom__ // __searchByDateTo__
          
```

    public function scopeSearchByField($query, $filed_name)
    {
        $query->when(request()->filled($filed_name), function ($qr) use ($filed_name) {
            if (request()->$filed_name) {
                $ids[] = request()->$filed_name;
                $qr->whereIn($filed_name, $ids);
            } else {
                $qr->where($filed_name, request()->$filed_name);
            }
        });
    }



    public function scopeSearchDateFrom($query, $filed_name, $from = null)
    {
        if ($from == null) {
            $from = 'from';
        }

        $query->when(request()->filled($from), function ($qr) use ($filed_name, $from) {
            $qr->where($filed_name, '>=', request()->$from);
        });
    }


    public function scopeSearchDateTo($query, $filed_name, $to = null)
    {
        if ($to == null) {
            $to = 'to';
        }

        $query->when(request()->filled($to), function ($qr) use ($filed_name, $to) {
            $qr->where($filed_name, '<=', request()->$to);
        });
    }
    
```
