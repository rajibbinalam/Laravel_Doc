```php
  
  use App\Models\SystemSetting;
  use Illuminate\Support\Facades\Cache;
  
  function active_menu($routeName, $class = 'active')
  {
      return \Illuminate\Support\Facades\Route::currentRouteName() === $routeName ? $class : '';
  }
  
  function system_setting()
  {
      return Cache::rememberForever('system_setting', function () {
          return SystemSetting::get();
      });
  }
  function setting($key)
  {
      return optional(system_setting()->where('key', $key)->first())->value;
  }
  
  /**
   *  Date Formater
   * @param $value
   * @param null $format
   * @return string
   */
  function fdate($value, $format = null){
      try {
          if ($value == '') {
              return '';
          }
          if ($format == null) {
              $format = 'Y-m-d';
          }
          return \Carbon\Carbon::parse($value)->format($format);
      } catch (\Throwable $th) {
          return $value;
      }
  }
  /**
   * Date Difference
   * @param $from
   * @param null $to
   * @param null $format
   */
  function dateDiff($from, $to = null, $format = null){
      try {
          if ($from == '') {
              return '';
          }
          if (!$to) {
              $to = now();
          }
          if ($format == null) {
              $format = 'Y-m-d';
          }
          return \Carbon\Carbon::parse($from)->diff(\Carbon\Carbon::now())->format('%yY- %mM-%dD');
      } catch (\Throwable $th) {
          return $from;
      }
  }
  
  function isTime($time){
      return preg_match("#([0-1]{1}[0-9]{1}|[2]{1}[0-3]{1}):[0-5]{1}[0-9]{1}#", $time);
  }
  
  
  function totalDaysInMonth($month){
      return \Carbon\Carbon::parse($month ?? date('Y-m'))->daysInMonth;
  }
  
  function firstOfMonth($month){
      return \Carbon\Carbon::parse($month ?? date('Y-m'))->firstOfMonth()->format('Y-m-d');
  }
  
  function dayNumber(string $dayName):int{
      $dayName = strtolower($dayName);
      if($dayName == 'saturday'){
          return 6;
      }else if($dayName == 'sunday'){
          return 0;
      }else if($dayName == 'monday'){
          return 1;
      }else if($dayName == 'tuesday'){
          return 2;
      }else if($dayName == 'wednesday'){
          return 3;
      }else if($dayName == 'thursday'){
          return 4;
      }else if($dayName == 'friday'){
          return 5;
      }
  }
  
  // GET OLD VALUE WHEN USING POST METHOD ON FORM
  function oldSelect($field_name, $value, $defaultValue = null): string{
      return old($field_name, $defaultValue) == $value ? 'selected' : '';
  }
  // GET REQUEST VALUE WHEN USING GET METHOD ON FORM
  function requestSelect($field_name, $value, $defaultValue = null): string
  {
      return request($field_name, $defaultValue) == $value ? 'selected' : '';
  }
  
  // CONVERT CURRENCY IN WORD
  function currencyToWords($num): string{
      // return str_replace('-', ' ', (new NumberToWords)->getCurrencyTransformer('en')->toWords(str_contains($num, '.') ? ((float)$num * 100) : $num, 'USD'));
      return '';
  }
  
  // CONVERT AMOUNT IN WORD
  function inWords($amount): string
  {
      try{
          $f = new NumberFormatter(locale_get_default(), \NumberFormatter::SPELLOUT);
          return ucwords(str_replace('-', ' ', $f->format($amount)));
      }catch(\Throwable $th){
          return '';
      }
  }
  function translateToBanglaDigits($input) {
      $englishDigits = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9'];
      $banglaDigits = ['০', '১', '২', '৩', '৪', '৫', '৬', '৭', '৮', '৯'];
      return str_replace($englishDigits, $banglaDigits, $input);
  }
  
  function numberToWordsBangla($number) {
      $eng_to_bn = array('1' => '১', '2' => '২', '3' => '৩', '4' => '৪', '5' => '৫', '6' => '৬', '7' => '৭', '8' => '৮', '9' => '৯', '0' => '০');
      $num_to_bd = array(
          '1' => 'এক', '2' => 'দুই', '3' => 'তিন', '4' => 'চার', '5' => 'পাঁচ', '6' => 'ছয়', '7' => 'সাত', '8' => 'আট', '9' => 'নয়',
          '1310' => 'দশ', '11' => 'এগারো', '12' => 'বারো', '13' => 'তেরো', '14' => 'চোদ্দ', '15' => 'পনেরো', '16' => 'ষোল', '17' => 'সতেরো', '18' => 'আটারো', '19' => 'ঊনিশ',
          '20' => 'বিশ', '21' => 'একুশ', '22' => 'বাইশ', '23' => 'তেইশ', '24' => 'চব্বিশ', '25' => 'পঁচিশ', '26' => 'ছাব্বিশ', '27' => 'সাতাশ', '28' => 'আটাশ', '29' => 'ঊনত্রিশ', '30' => 'ত্রিশ',
          '31' => 'একত্রিশ', '32' => 'বত্রিশ', '33' => 'তেত্রিশ', '34' => 'চৌত্রিশ', '35' => 'পঁয়ত্রিশ', '36' => 'ছত্রিশ', '37' => 'সাঁইত্রিশ', '38' => 'আটত্রিশ', '39' => 'ঊনচল্লিশ',
          '40' => 'চল্লিশ', '41' => 'একচল্লিশ', '42' => 'বিয়াল্লিশ', '43' => 'তেতাল্লিশ', '44' => 'চুয়াল্লিশ', '45' => 'পঁয়তাল্লিশ', '46' => 'ছেচল্লিশ', '47' => 'সাতচল্লিশ',
          '48' => 'আটচল্লিশ', '49' => 'ঊনপঞ্চাশ', '50' => 'পঞ্চাশ', '51' => 'একান্ন', '52' => 'বায়ান্ন', '53' => 'তিপ্পান্ন', '54' => 'চুয়ান্ন', '55' => 'পঞ্চান্ন',
          '56' => 'ছাপ্পান্ন', '57' => 'সাতান্ন', '58' => 'আটান্ন', '59' => 'ঊনষাট', '60' => 'ষাট', '61' => 'একষট্টি', '62' => 'বাষট্টি', '63' => 'তেষট্টি',
          '64' => 'চৌষট্টি', '65' => 'পঁয়ষট্টি', '66' => 'ছেষট্টি', '67' => 'সাতষট্টি', '68' => 'আটষট্টি', '69' => 'ঊনসত্তর', '70' => 'সত্তর', '71' => 'একাত্তর',
          '72' => 'বাহাত্তর', '73' => 'তিয়াত্তর', '74' => 'চুয়াত্তর', '75' => 'পঁচাত্তর', '76' => 'ছিয়াত্তর', '77' => 'সাতাত্তর', '78' => 'আটাত্তর', '79' => 'ঊনআশি',
          '80' => 'আশি', '81' => 'একাশি', '82' => 'বিরাশি', '83' => 'তিরাশি', '84' => 'চুরাশি', '85' => 'পঁচাশি', '86' => 'ছিয়াশি', '87' => 'সাতাশি', '88' => 'আটাশি',
          '89' => 'ঊননব্বই', '90' => 'নব্বই', '91' => 'একানব্বই', '92' => 'বিরানব্বই', '93' => 'তিরানব্বই', '94' => 'চুরানব্বই', '95' => 'পঁচানব্বই', '96' => 'ছিয়ানব্বই', '97' => 'সাতানব্বই', '98' => 'আটানব্বই', '99' => 'নিরানব্বই'
      );
      $num_to_bn_decimal = array(
          '0' => 'শূন্য ', '1' => 'এক ', '2' => 'দুই ', '3' => 'তিন ', '4' => 'চার ', '5' => 'পাঁচ ', '6' => 'ছয় ', '7' => 'সাত ', '8' => 'আট ', '9' => 'নয় '
      );
      $hundred = 'শত';
      $thousand = 'হাজার';
      $lakh = 'লক্ষ';
      $crore = 'কোটি';
  
      $bn_number = strtr($number, $eng_to_bn);
  
      // Split the number into decimal and integer parts
      $parts = explode('.', $bn_number);
  
      $integerPart = $parts[0];
      $decimalPart = isset($parts[1]) ? $parts[1] : '';
  
      $integerWord = strtr($integerPart, $num_to_bd);
      $decimalWord = strtr($decimalPart, $num_to_bn_decimal);
  
      $result = $integerWord;
  
      if (!empty($decimalWord)) {
          $result .= ' দশমিক ' . $decimalWord;
      }
  
      return $result;
  }
  function getInWord($number)
  {
      $decimal = round($number - ($no = floor($number)), 2) * 100;
      $hundred = null;
      $digits_length = strlen($no);
      $i = 0;
      $str = array();
      $words = array(0 => '', 1 => 'One', 2 => 'Two',
          3 => 'Three', 4 => 'Four', 5 => 'Five', 6 => 'Six',
          7 => 'Seven', 8 => 'Eight', 9 => 'Nine',
          10 => 'Ten', 11 => 'Eleven', 12 => 'Twelve',
          13 => 'Thirteen', 14 => 'Fourteen', 15 => 'Fifteen',
          16 => 'Sixteen', 17 => 'Seventeen', 18 => 'Eighteen',
          19 => 'Nineteen', 20 => 'Twenty', 30 => 'Thirty',
          40 => 'Forty', 50 => 'Fifty', 60 => 'Sixty',
          70 => 'Seventy', 80 => 'Eighty', 90 => 'Ninety');
      $digits = array('', 'Hundred','Thousand','Lakh', 'Crore');
      while( $i < $digits_length ) {
          $divider = ($i == 2) ? 10 : 100;
          $number = floor($no % $divider);
          $no = floor($no / $divider);
          $i += $divider == 10 ? 1 : 2;
          if ($number) {
              $plural = (($counter = count($str)) && $number > 9) ? 's' : null;
              $hundred = ($counter == 1 && $str[0]) ? ' and ' : null;
              $str [] = ($number < 21) ? $words[$number].' '. $digits[$counter]. $plural.' '.$hundred:$words[floor($number / 10) * 10].' '.$words[$number % 10]. ' '.$digits[$counter].$plural.' '.$hundred;
          } else $str[] = null;
      }
      $Taka = implode('', array_reverse($str));
      $poysa = ($decimal) ? " and " . ($words[$decimal / 10] . " " . $words[$decimal % 10]) . ' ' : '';
      $currency = isset(optional(auth()->user()->businessProfile)->currency) ? optional(auth()->user()->businessProfile)->currency : "৳";
  
      // return ($Taka ? $Taka  : '') . $poysa .$currency . ' only ' ;
      return $Taka ? $Taka  : '';
  }
  
  
  // GET PERCENT
  function getPercent($total_amount, $amount)
  {
      if ($total_amount < 1) {
          return 0;
      }
  
      return ($amount * 100) / $total_amount;
  }
  
  // GET PERCENT AMOUNT
  function getAmountOfXPercent($total_amount, $percent)
  {
      return ($total_amount * $percent) / 100;
  }
  // GET VALIDATION ERROR MESSAGE
  function getValidationErrorMessage($name)
  {
      return view('partials._error-message', ['name' => $name])->render();
  }
  // GET DATE IN ARRAY BETWEEN TWO GIVEN DATE
  function getDateArray($fromDate, $toDate)
  {
      $toDate = \Carbon\Carbon::parse($toDate)->addDay();
      $period = new DatePeriod(
          new DateTime($fromDate),
          new DateInterval('P1D'),
          new DateTime($toDate)
      );
  
      $dates = [];
      foreach ($period as $key => $value) {
  
          $dates[] = $value->format('Y-m-d');
      }
      return $dates;
  }
  function calculateTime($times)
  {
      $minutes = 0;
  
      try {
          foreach ($times as $time) {
              $time = number_format((float)$time, 2, '.', '');
              if ($time != '' || $time != null) {
                  try {
                      list($hour, $minute) = explode('.', $time);
                      $minutes += $hour * 60;
                      $minutes += $minute;
                  } catch (\Exception $ex) {
                      $minutes += 0;
                  }
              }
          }
  
          $hours = floor($minutes / 60);
          $minutes -= $hours * 60;
  
      } catch (\Throwable $th) {
          $hours  = 0;
          $minutes = 0;
      }
  
      return sprintf('%02d.%02d', $hours, $minutes);
  }
  
  function numberFormat($number, $limit = null){
      if($limit == null) $limit = 2;
      return number_format($number, $limit, '.'. '');
  }
  
  
  /**
   * get timezone list
   *
   * @return array
   * @throws Exception
   */
  function timezoneList(): array
  {
      $timezoneIdentifiers = DateTimeZone::listIdentifiers();
      $utcTime             = new DateTime('now', new DateTimeZone('UTC'));
  
      $tempTimezones = [];
      foreach ($timezoneIdentifiers as $timezoneIdentifier) {
          $currentTimezone = new DateTimeZone($timezoneIdentifier);
  
          $tempTimezones[] = [
                  'offset'     => $currentTimezone->getOffset($utcTime),
                  'identifier' => $timezoneIdentifier,
          ];
      }
      usort($tempTimezones, function ($a, $b) {
          return ($a['offset'] == $b['offset'])
                  ? strcmp($a['identifier'], $b['identifier'])
                  : $a['offset'] - $b['offset'];
      });
  
      $timezoneList = [];
      foreach ($tempTimezones as $tz) {
          $sign                            = ($tz['offset'] > 0) ? '+' : '-';
          $offset                          = gmdate('H:i', abs($tz['offset']));
          $timezoneList[$tz['identifier']] = '(UTC '.$sign.$offset.') '.
                  $tz['identifier'];
      }
  
      return $timezoneList;
  }
```
