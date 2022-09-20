            __Html to Text__
           
1. Strip Tags

```
  $html = "
      <body>
          <p>
              This is a body of text encapsulated in <b>HTML</b>.
              <b>Let's parse it!</b>
          </p>
      </body>";

  echo strip_tags($html);
  
  Result: This is a body of text encapsulated in HTML. Let's parse it!
```
2. Install Package:

```
composer require html2text/html2text
```
```
$html = "
    <body>
        <p>
            This is a body of text encapsulated in <b>HTML</b>.
        </p>
    </body>";

$html2TextConverter = new \Html2Text\Html2Text($html);

echo $html2TextConverter->getText();
```
