If you know the order of your numeric and alphabetic substrings, then``` sscanf()``` is a perfect tool.

Code: (Demo)
```
var_export(sscanf('12jan', '%d%s'));

```
Output:
```
array (
  0 => 12,
  1 => 'jan',
)
```
Notice how 12 is conveniently cast as an integer as well.

```sscanf()``` also allows individual variables to be assigned if desired ($day and $month) as the 3rd and 4th parameters.
