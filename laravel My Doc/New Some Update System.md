__1. CHUNK()__
```
@foreach($users->chunk(2) as $row)
    <div class="grid__row">
        @foreach($row as $user)
            <div class="grid__item">
                {{ $user->name}}
            </div>
        @endforeach
    </div>
@endforeach

RESULT: 
if User= collection of 6 users.
1.
  i. user1
  ii. user2
2.
  i. user3
  ii. user4
3.
  i. user5
  ii. user6
```
