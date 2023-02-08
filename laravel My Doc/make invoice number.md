### Make Invoice Number with extra zero( 0 ) and Date, Year
```php
        if($this->saleReturnExchange){
        
            $sale_id = sprintf("%06d", $this->saleReturnExchange->id);
            
            SaleReturnExchange::find($this->saleReturnExchange->id)->update([
                'invoice_no'    => 'SREX' . '-' . date('y') . $sale_id,
            ]);
        }
```
