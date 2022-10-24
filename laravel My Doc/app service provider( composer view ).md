1.        
```
	$WebMaintenence = WebMaintenence::first();
        $general = GeneralSetting::first();
        $loader = Loader::first();
        $contact = Contact::first();
        $footer1 = UseFullLink1st::first();
        $footer2 = UseFullLink2nd::first();
        View::share(['contact'=> $contact, 'footer1'=>$footer1, 'footer2'=>$footer2,'general'=> $general, 'loader'=>			$loader,'WebMaintenence'=>$WebMaintenence]);

        $socials = SocialLink::all();

        view()->composer('partials.header',function($view){
            $view->with([
                'categories' => Category::select('id','name')->with('subCategories:id,name,category_id')->get()
            ]);
        });
       View::share(['socials' => $socials]);
```


2. 
```

View::composer('*', function ($view) {
    if ($view->getName() != 'partials.not-this-view') { // Except:- (partials.not-this-view) View
        $view->with('variable', 'Set variable');
    }
});
```

3. 
```

View::composer('*', function ($view) {
    if (!in_array($view->getName(), ['partials.view-1', 'partials.view-1', 'other-view']) {   // Except:- Multiple View
        $view->with('variable', 'Set variable');
    }
});
```
