__PrintThis()__ Funstion
```
$("#printMe").click(function () {

$('#print-it').printThis({
            importCSS: true,
            importStyle: true,
            loadCSS: "/assets/css/print_rules_page1.css"
            });
});
```

it need to use inportCSS and loadCSS with the printThis() jquery plugin

__CSS ("loadCSS" load file print_rules_page1.css)__

```
@media print 
{
  #no-print-this,#no-print-this2 *{
  display: none !important;
  }
}
```
