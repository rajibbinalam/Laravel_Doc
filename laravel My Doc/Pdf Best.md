__DomPDF is not Support Bangla__

__mPDF for Bangla Support__

GitHub : https://github.com/mccarlosen/laravel-mpdf


__make a blade(html) file to like pdf Page__ :::  (__stream()__)

```
         $pdfInvoice=PDF::loadView('backend.member-wise-payment.member-payment-paid-invoice',
            [
                'memberPaidPaymentInfo'=>$memberPaidPaymentInfo,
                'paidAmountinfo'=>$paidAmountinfo,
                'companyinfo'=>$companyinfo,
            ]);
        return $pdfInvoice->stream();
```

__SHow Image in PDF __
```
<img src="backend/img/logo/{{ $companyinfo->Logo }}">
```
