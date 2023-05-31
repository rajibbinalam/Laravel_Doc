## Get Data / Response from External API
#### controller/ View: 
```php
$response = Http::get('https://jsonplaceholder.typicode.com/posts');
```
#### view: $response['title'];




#### for Older Version:

```php
$url = 'http://smpp.ajuratech.com/portal/sms/smsConfiguration/smsClientBalance.jsp?client='.env('CLIENT_NAME_FOR_SMS_BALANCE');

$json = file_get_contents($url);

$json_data = json_decode($json, true);

if($json_data){
    $json_data= $json_data;
}
else{
    $json_data = ['Balance'=>'Invalide', 'CreditLimit'=> 'Invalide'];
}
```
