### HasManyThrough and HasOneThrough Relationship

### Situation: 
  1. 3 Models : Channel, Video, Commend
  2. Channel hasMany Videos  && Video hasMany Commends
### Relations:

#### Has Many Through: 
  i want to get all Commends of a Channel Throw the Videos.
  
```in Channel Model```
```php
      public function commends(): HasManyThrough
    {
        return $this->hasManyThrough(Commend::class, Video::class);
        // 1st (Commend) Model is which we want to access
        // 2nd (Video) Model is Intermediate Model
    }
```
- [ ] if database field name is not convenient with the model name THEN =>
```php
      public function commends(): HasManyThrough
    {
        return $this->hasManyThrough(
                Commend::class,
                Video::class,
                'channel_id',  // from videos Table
                'video_id',   // from commends Table
                'id',
                'id'
              );
    }
```


#### Has One Through
  This relationship is almost exactly the same as a ```hasMany()``` relationship, although in this situation you need to be sure that there is only one final item

```php
    public function commend(): HasOneThrough
    {
        return $this->hasOneThrough(Commend::class, Video::class);
    }
```

Here, you'll get only one data (commend) from hasOneThrough Relationship
