
1. {{-- selec2 cdn --}}

<link href="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/css/select2.min.css" rel="stylesheet" />


2.
<script src="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/js/select2.min.js"></script>


3.       
<script>
        $(document).ready(function() {
            // Select2 Multiple
            $('.select2-multiple').select2({
                placeholder: "Select",
                allowClear: true
            });

        });

    </script>


		******----------------  Check----------------  ****


 <select class="select2-multiple form-control" name="tags[]" multiple="multiple"
                id="select2Multiple">
                <option value="tag1">tag1</option>
                <option value="tag2">tag2</option>
                <option value="tag3">tag3</option>               
              </select>
