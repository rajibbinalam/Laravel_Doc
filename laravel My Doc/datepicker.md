<a href="https://uxsolutions.github.io/bootstrap-datepicker/?markup=input&format=&weekStart=&startDate=&endDate=&startView=0&minViewMode=0&maxViewMode=4&todayBtn=false&clearBtn=false&language=en&orientation=auto&multidate=&multidateSeparator=&keyboardNavigation=on&forceParse=on&beforeShowDay=on&beforeShowMonth=on#sandbox">https://uxsolutions.github.io/bootstrap-datepicker/?markup=input&format=&weekStart=&startDate=&endDate=&startView=0&minViewMode=0&maxViewMode=4&todayBtn=false&clearBtn=false&language=en&orientation=auto&multidate=&multidateSeparator=&keyboardNavigation=on&forceParse=on&beforeShowDay=on&beforeShowMonth=on#sandbox</a>


 ```
 <link href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap-datepicker/1.2.0/css/datepicker.min.css" rel="stylesheet">

<script src="https://cdnjs.cloudflare.com/ajax/libs/bootstrap-datepicker/1.2.0/js/bootstrap-datepicker.min.js"></script>
```


__Year, Month, Date Picker__
```
        $("#datepicker").datepicker({
            format: "yyyy",
            viewMode: "years",
            minViewMode: "years",
            autoclose: true
        });
        
         $("#datepicker").datepicker({
            format: "yyyy-mm",
            viewMode: "months",
            minViewMode: "months",
            autoclose: true
        });
        
         $("#datepicker").datepicker({
            format: "yyyy-mm-dd",
            viewMode: "yyyy-mm-dd",
            minViewMode: "yyyy-mm-dd",
            autoclose: true
        });
```

__Features: __

```
date('Y-m-t')     //  Get Last Date of The Month

date('l')     // Day Name of Date Ex: Friday

```
