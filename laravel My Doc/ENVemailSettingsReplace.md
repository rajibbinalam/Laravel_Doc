#### 1. Make Form for submit ENV email Credentials 
#### 2. Pass those Credentials to Controller By Route
#### 3. Controller Be Like this Code for Replace ENV Email Credentials:

```php
public function mailSettingStore(Request $request){
	$data = $request->all();

	//writting mail info in .env file
	$path = base_path('.env');   // Path of ENV
	
		// -------------- Search Those in ENV
	$searchArray = array('MAIL_HOST="' . env('MAIL_HOST') . '"', 'MAIL_PORT=' . env('MAIL_PORT'), 'MAIL_FROM_ADDRESS="' . env('MAIL_FROM_ADDRESS') . '"', 'MAIL_FROM_NAME="' . env('MAIL_FROM_NAME') . '"' , 'MAIL_FROM_EMAIL="' . env('MAIL_FROM_EMAIL') . '"', 'MAIL_USERNAME="' . env('MAIL_USERNAME') . '"', 'MAIL_PASSWORD="' . env('MAIL_PASSWORD') . '"');
	//    return $searchArray;
	
		//------------- Replace Those ENV setting
	$replaceArray = array('MAIL_HOST="' . $data['mail_host'] . '"', 'MAIL_PORT=' . $data['port'], 'MAIL_FROM_ADDRESS="' . $data['mail_address'] . '"', 'MAIL_FROM_NAME="' . $data['mail_name'] . '"' , 'MAIL_FROM_EMAIL="' . $data['email_name'] . '"', 'MAIL_USERNAME="' . $data['mail_address'] . '"', 'MAIL_PASSWORD="' . $data['password'] . '"');
	// return $replaceArray;
	
	file_put_contents($path, str_replace($searchArray, $replaceArray, file_get_contents($path)));
	
	return redirect()->back()->with('message', 'Data updated successfully');
}
```

### NB:::  Maintain serial with ( ENV , $searchArray , $replaceArray ) - Credentials Must serialized
