https://packagist.org/packages/carlos-meneses/laravel-mpdf

git hub: https://github.com/mccarlosen/laravel-mpdf


font: Nikosh

For font suport EDIT: ```confige/pdf.php```

'auto_language_detection'    => true,



__For Bangla Language Support__

  DOC: URL: http://bonstutorial.com/bangla-font-in-pdf-laravelmpdf-package/

1. Download Nikosh.ttf (url: https://www.omicronlab.com/bangla-fonts.html)
2. Go to <b>project/vendor/mpdf/mpdf/src/Config/FontVariables.php</b> ,open FontVariables.php and search for ‘indics’ ,then after pothana2000 ,add follwoing code
```
"pothana2000" => [
    'R' => "Pothana2000.ttf",
    'useOTL' => 0xFF,
  ],
  "nikosh" => [
    'R' => "Nikosh.ttf",
    'useOTL' => 0xFF,
  ],
```

In Blade File: 

__stream()__ for Pdf View

__download('doc.pdf')__ for Download
