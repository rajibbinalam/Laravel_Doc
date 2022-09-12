1. Ck Editor:

2. Tiny Editor: 

    __ -> Script CDN :__
    
```
    <script src="https://cdnjs.cloudflare.com/ajax/libs/tinymce/6.0.3/tinymce.min.js" integrity="sha512-DB4Mu+YChAdaLiuKCybPULuNSoFBZ2flD9vURt7PgU/7pUDnwgZEO+M89GjBLvK9v/NaixpswQtQRPSMRQwYIA==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
```

    __ ->script :__
```
    tinymce.init({
            selector: 'textarea#tinyEditor',
            plugins: [
                'a11ychecker', 'advlist', 'advcode', 'advtable', 'print', 'hr', 'autolink', 'pagebreak', 'checklist', 'export',
                'lists', 'link', 'image', 'charmap', 'preview', 'anchor', 'searchreplace', 'visualblocks',
                'powerpaste', 'fullscreen', 'formatpainter', 'insertdatetime', 'media', 'code', 'nonbreaking', 'table', 'help',
                'wordcount'
            ],

            toolbar: 'undo redo | styleselect | a11ycheck casechange blocks | bold italic backcolor | alignleft aligncenter alignright alignjustify | ' +
                'bullist numlist checklist outdent indent | link image | print preview media fullscreen | ' +
                'forecolor backcolor emoticons | removeformat | code table help | help',
            menu: {
                favs: {title: 'My Favorites', items: 'code visualaid | searchreplace | emoticons'}
            },
            menubar: 'favs file edit view insert format tools table help',
            content_style: 'body { font-family:Helvetica,Arial,sans-serif; font-size:14px }'
        });
```

3. Summer Note:

    __-> Link: https://summernote.org/getting-started/#compiled-css-js __

    __Support : __
        1. Image On text
        2. Bootstrap 4, 5
        3. table design 

```
$('#summernote').summernote({
        height: 400
    });
```
