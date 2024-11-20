### Quill JS Editor
  ##### This Document is just for simple example. For Advance and high cinfiguration See the Official Documentation.
  <a href="https://quilljs.com/docs/quickstart" target="__blank">https://quilljs.com/docs/quickstart</a>
### Short Documentation

#### Assest
```blade
<link href="https://cdn.quilljs.com/1.3.6/quill.snow.css" rel="stylesheet">
<script src="https://cdn.quilljs.com/1.3.6/quill.js"></script>

<!-- OR Newst Version -->

<link href="https://cdn.jsdelivr.net/npm/quill@2.0.2/dist/quill.core.css" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/quill@2.0.2/dist/quill.core.js"></script>
```

#### Editor in blade
```blade
<div id="editor-container"></div>
```

#### Initialize Editor
```js
// Initialize Quill editor
var quill = new Quill('#editor-container', {
  theme: 'snow', // This gives a clean, minimalistic style (like Medium)
  modules: {
    toolbar: [
      [{ 'header': '1' }, { 'header': '2' }, { 'font': [] }],
      [{ 'list': 'ordered'}, { 'list': 'bullet' }],
      ['bold', 'italic', 'underline'],
      ['link'],
      ['image'],
      [{ 'align': [] }],
      [{ 'indent': '-1'}, { 'indent': '+1' }],
      [{ 'direction': 'rtl' }],
      ['blockquote', 'code-block'],
      [{ 'color': [] }, { 'background': [] }],
      [{ 'script': 'sub'}, { 'script': 'super' }],
      ['clean']  // This button clears the content (like Medium)
    ]
  },
  clipboard: {
      matchVisual: false,
  },
  imageDrop: true, // To handle images dropped directly into the editor
});
```
