1. 
 <link href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap-datepicker/1.2.0/css/datepicker.min.css" rel="stylesheet">


2. 

<script src="https://cdnjs.cloudflare.com/ajax/libs/bootstrap-datepicker/1.2.0/js/bootstrap-datepicker.min.js"></script>



3. 
```
 $("#datepicker").datepicker({
            format: "yyyy",
            viewMode: "years",
            minViewMode: "years",
            autoclose: true //to close picker once year is selected
        });
```

__ Get Last Date of The Month: __

```
 <?php
    echo date('Y-m-t');
 ?>
```
