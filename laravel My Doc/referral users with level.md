### 1. User have multiple refer users and each of refer users have multiple refer users as like Tree
#### Like this Image:

<img width="935" alt="Refer Tree" src="https://github.com/user-attachments/assets/0adb5398-5b67-46b1-9ae3-1358aade1ec2">


### 2. User Model:
```php
    public $allusers = [];
    
    public function referral(){
        return $this->belongsTo(User::class, 'referral_id');
    }

    // Getting with recursive
    public function referralUsers($id, $currentLevel = 1){
        $users = $this->getUsers($id);
        if ($users['status']) {
            $this->allusers[$currentLevel] = $users['user'];
            $currentLevel++;
            $this->referralUsers($users['ids'], $currentLevel);
        }
        return $this->allusers;
    }
    
    public function scopeLevel()
    {
        $count = 0;
        $user_id = $this->id;
        while ($user_id != null) {
            $user = User::where('referral_id', $user_id)->first();
            if (!$user) {
                break;
            } else {
                $user_id = $user->id;
                $count++;
            }
        }
        return $count;
    }
    
    public function getUsers($id)
    {
        if (isset($id)) {
            $data['user'] = User::whereIn('referral_id', $id)->get(['id', 'firstname', 'lastname', 'username', 'email', 'phone_code', 'phone', 'referral_id', 'created_at']);
            if (count($data['user']) > 0) {
                $data['status'] = true;
                $data['ids'] = $data['user']->pluck('id');
                return $data;
            }
        }
        $data['status'] = false;
        return $data;
    }
```

### 3. Helper Function:
```php
function getLevelUser($id){
    $ussss = new \App\Models\User();
    return $ussss->referralUsers([$id]);
}
```

### 4. Call Helper Function
```php
return getLevelUser($id);
```

