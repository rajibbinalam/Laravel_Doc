## Send Email From Contact Us Form
#### Login to the MailTrap First
#### Complete Mailtrap Cradentials

1.  make contact form(view),
2.  CRUD operation with Contact Form {Controller}

```php
public function ContactUsSubmit(Request $request)
{
    $request->validate([
        '*' => 'required',
    ]);

    $data = array(
        'name'      =>  $request->name,
        'email'   =>   $request->email,
        'message'   =>   $request->message,
        'phone'   =>   $request->phone,
        'subject'   =>   $request->subject,
    );

    //  Send mail to admin
    Mail::to('smartsoft@gmail.com')->send(new Contact($data)); 			// [ Contact = Mail Contact ]

    return redirect()->route('ContactUs');
}
```



3.  make Mail.
```sh
php artisan make:mail Contact
```

```php

namespace App\Mail;

use Illuminate\Bus\Queueable;
use Illuminate\Contracts\Queue\ShouldQueue;
use Illuminate\Mail\Mailable;
use Illuminate\Queue\SerializesModels;

class Contact extends Mailable
{
    use Queueable, SerializesModels;
    public $data;		//---------------------------------------[Add ]
    /**
     * Create a new message instance.
     *
     * @return void
     */
    public function __construct($data)	//------------------------------[Add - $data ]
    {
        $this->data = $data;		//------------------------------[ Add this line ]
    }

    /**
     * Build the message.
     *
     * @return $this
     */
    public function build()
    {
        return $this->view('backend.email_settings.emails')->from($this->data['email'])->with('data');	//----------[ Set View , with('data') ]
    }
}
```

4.  make View- [emails.email]--- for design email body
```blade
<p>Hi, This is {{ $data['name'] }}</p>
<p>Subject : {{ $data['subject'] }}</p>
<p>Phone : {{ $data['phone'] }}</p>
<p>Message : {{ $data['message'] }}.</p>
```
