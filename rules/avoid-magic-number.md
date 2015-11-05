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

Магические числа порождают проблемы когда они используются в двух разных местах, и обновляются только в одном месте.

0, 1, 2 and 100 are often regarded as exceptions, as they are so often used. However, it is also a good idea to consider them as magic number and provide a better name for them : for example, 0 and 1 may be used and confused as `false` and `true`.

Числа 0, 1, 2 и 100 являются исключениями, так как они часто используются. Однако, это хороший подход, рассматривать их в качестве магических чисел, например, 0 и 1 могут спутать с `false` и `true`.

Magic numbers are useful in unit tests, where a wide range of valid and invalid values must be tested to check the behavior of the code.
Магические числа полезны в unit тестах, где широкий диапазон валидных и невалидных значений должны использоваться чтобы проверить поведение кода.

It is recommended to provide explicit constant names for literals as often as possible. 0 and 1 should be considered too.
Рекомендуется задать явные имена для чисал так часто, как это возможно. 0 и 1 тоже следует именовать.

## Подробнее о правиле

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

## Дополнительная литература

* [Магическое число (программирование)] (https://ru.wikipedia.org/wiki/%D0%9C%D0%B0%D0%B3%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B5_%D1%87%D0%B8%D1%81%D0%BB%D0%BE_(%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5))
