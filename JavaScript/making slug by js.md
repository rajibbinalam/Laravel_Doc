# IT CAN'T AVOID (# $ % & * ?) SPACIAL CHARACTER

```javascript
function mytitle() {
    var title = document.getElementById("title");
    var slug = title.value.replace(/\s+/g, '-').toLowerCase()
    document.getElementById("slug").value = slug;
}
```


# IT CAN AVOID (# $ % & * ?) SPACIAL CHARACTER

```javascript
function HeadingSlug(){
      var heading = document.getElementById('heading').value;
      var titleSlug = heading.replace(/[^a-zA-Z0-9]/ig, '-').toLowerCase();
      var slug = titleSlug.replace(/\s+/g,'-').toLowerCase();
      document.getElementById('slug').value = slug;
 }
```
# IT will remove special characters and multiple dash (-)
```php
    function HeadingSlug(){
        let heading = document.getElementById('title').value;
        let titleSlug = heading.trim().replace(/\s+/g, '-').toLowerCase();
        titleSlug = titleSlug.replace(/[^a-zA-Z0-9\-]/g, '');
        // let slug = titleSlug.replace(/-$/, '');
        
        let slug = titleSlug.replace(/-{2,}/g, '-');

        // Remove trailing dash, if any
        slug = slug.replace(/-$/, '');
        document.getElementById('slug').value = slug;
    }
```
