<!-- Good Practices -->
# Избегайте магических чисел

Магическое число - это число, которое жестко прописано в коде, тогда как он может иметь особое или связанный значение, которое понять сразу нельзя.

В дальнейшем, например, магическое число нужно будет найти и изменить.

```php
<?php

if (strlen($password) < 10) { // 10 это магическое число, которое может изменится в любое время. 
	$password['status'] = 33; // это номер ошибки, другое магическое число
	$password['checked'] += 1; // это не магическое число: он содержит только количество проверок пароля
}

?>
```

Magic numbers will raise problems when they appear in two different locations, and are updated only once. 

0, 1, 2 and 100 are often regarded as exceptions, as they are so often used. However, it is also a good idea to consider them as magic number and provide a better name for them : for example, 0 and 1 may be used and confused as `false` and `true`.

Magic numbers are useful in unit tests, where a wide range of valid and invalid values must be tested to check the behavior of the code.

It is recommended to provide explicit constant names for literals as often as possible. 0 and 1 should be considered too.

## Rule Details

This rules targets literals within comparisons, math expressions or assignations.

The following code is considered a warning:

```php
<?php
if ($value == 1) {  // magic number
	$value *= 1.206;   // magic number for VAT in some countries
}

if (3 > $value) { 
	// DoSomething()
}
?>
```

The following pattern is considered legit:

```php
<?php

$percentage /= 100; // classic percentage

$count += 1; // simple increment

?>
```

<!--
## When Not To Use It

-->

## Further Reading 

* [Magic number (programming)] (http://en.wikipedia.org/wiki/Magic_number_%28programming%29)
