#IT CAN'T AVOID (# $ % & * ?) SPACIAL CHARACTER

```javascript
function mytitle() {
    var title = document.getElementById("title");
    var slug = title.value.replace(/\s+/g, '-').toLowerCase()
    document.getElementById("slug").value = slug;
}
```


#IT CAN AVOID (# $ % & * ?) SPACIAL CHARACTER

```javascript
function HeadingSlug(){
      var heading = document.getElementById('heading').value;
      var titleSlug = heading.replace(/[^a-zA-Z0-9]/ig, '-').toLowerCase();
      var slug = titleSlug.replace(/\s+/g,'-').toLowerCase();
      document.getElementById('slug').value = slug;
 }
```
