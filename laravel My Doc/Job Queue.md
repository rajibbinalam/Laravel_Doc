__Laravel Queue run and implements with event listeners__

	1. Make Queue table: ```php artisan queue:table``` and Migrate the Table
	2. Je Mail Queueable hobe Oitar Class e ```class NewsEventMail extends Mailable implements ShouldQueue```
	3. run this command: ```php artisan queue:listen```
	4. Start work queue will auto.