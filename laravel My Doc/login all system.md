#### Login with email/phone/username and password

```php
 $request->validate([
                'email'     => 'required',
                'password'  => 'required',
            ]);

            // $credentials = $request->only('email', 'password');
            $field = filter_var($request->input('email'), FILTER_VALIDATE_EMAIL) ? 'email' : 'phone';

            if (Auth::attempt([$field => $request->email, 'password' => $request->password])) {
                return redirect()->intended('dashboard');
            }
            return redirect("login")->withSuccess('Oppes! You have entered invalid credentials');
```
