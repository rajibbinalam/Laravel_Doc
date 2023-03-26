#### DomPDF is not Support Bangla

#### mPDF for Bangla Support

GitHub : https://github.com/mccarlosen/laravel-mpdf


##### make a blade(html) file to like pdf Page :::  (__stream()__)

```php
         $pdfInvoice=PDF::loadView('backend.member-wise-payment.member-payment-paid-invoice',
            [
                'memberPaidPaymentInfo'=>$memberPaidPaymentInfo,
                'paidAmountinfo'=>$paidAmountinfo,
                'companyinfo'=>$companyinfo,
            ]);
        return $pdfInvoice->stream();
```

#### SHow Image in PDF
```php
<img src="backend/img/logo/{{ $companyinfo->Logo }}">
```



#### if Having issues:
1. undifind index : ____ 
sol: maybe there are table standard does not maintain as well. LIKE: table->thead->th and table->tbody->td;
