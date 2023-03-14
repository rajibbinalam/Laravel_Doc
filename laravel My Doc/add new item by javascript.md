#### 1. Add New Item by click button ------[ LIKE: product have so many color with defferent prices -- click to show new color picker and price ]

```javascript
$(document).ready(function () {
	var counter = 0;
	$(document).on("click",".addeventmore", function(){
	var whole_extra_item_add = $("#whole_extra_item_add").html();
	$(this).closest(".add_item").append(whole_extra_item_add);
	counter++;
	});

	$(document).on("click",".removeeventmore", function(event){
    $(this).closest(".delete_whole_extra_item_add").remove();
    counter -= 1;
	});


	// tinymce.init({selector:'.textarea'});
});
```


