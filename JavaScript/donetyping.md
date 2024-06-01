```javascript

(function($) {
        $.fn.donetyping = function(callback){
            var _this = $(this);
            var x_timer;
            _this.keyup(function (){
                clearTimeout(x_timer);
                x_timer = setTimeout(clear_timer, 1000);
            });

            function clear_timer(){
                clearTimeout(x_timer);
                callback.call(_this);
            }
        }
    })(jQuery);

    $('#size').donetyping(function(callback){
        let size = $(this).val()

        // let measurement = size.split(/ +/)
        let measurement = size.split(/[Xx]+/)

        let area = parseInt(measurement[0]) * parseInt(measurement[1]);
        let size_in_sft = (area / 144).toFixed(6);

        if($('#has-box').is(':checked'))
        {
            $('#pcs-sqt').val(size_in_sft);
        }
    });
    
```
