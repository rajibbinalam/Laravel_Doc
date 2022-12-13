__Update ```AcademicInfo``` table data with ```Student``` table data which is related__
```
AcademicInfo & Student Tables relation by one To one
```
__Update Both tables Data using map()__
```
$std = AcademicInfo::ownBranch()
                  ->current()
                  ->whereIn('id',$ids)
                  ->get()
                  ->map(function ($academic) {
                      $academic->update(['session_type' => 'archive']);
                      $academic->student->update(['status' => 'Passed']);
                  });
```

