<!-- Good Practices -->
# Всегда используйте точку с запятой

PHP использует точку с запятой `;` для разделения двух инструкций.

```php
<?php

$a = 'a';
echo $a;

?>
```

Иногда, точка с запятой не обязательна в конце инструкции. например:

```php
<?php
	echo 'a' 
?>
```
Здесь инструкция `echo 'a'` будет автоматически закрыта закрывающими символами PHP `?>` 

Иногда, если `;` пропущена, PHP запускает инструкцию на одной линии и заканчивает на следующей.

```php
<?php

$a = f() or 
	// $a = b()      // Просто комментарий
if ($condition) {}	// Здесь 'if' зависит от результата вызова функции f()
	
echo 
print 'b';
// Будет выведено b

?>
```
`continue` и `break` не принимает значений (по умолчанию 1) или результат следующего выражения (от PHP 5.4) : 

```php
<?php

for ( $i = 0; $i < 5; ++$i )
{
    if ( $i == 2 )
        continue
    print "$i\n";
    // Неожиданный результат
}

?>
```
There are quite some instructions that may overflow to the next line, like all operators, and : 
* all operators (math, comparison, logical...)
* echo
* print
* include and include_once
* require and require_once
* exit

This rules doesn't require the adding of extra semicolon when they are not needed.

```php
<?php

for ( $i = 0; $i < 5; ++$i ) { }; // useless semicolon

class x { }; // useless semicolon

?>
```

It is recommended to make sure that all required semicolon are always set, even if they are not compulsory.

## Rule Details

The following patterns are considered warnings:

```php
<?php
echo $a
?>
<?= 3 ?>
```

The following code is not considered warnings:

```php
<?php
include 
	'/some/file.php';
?>
```

<!--
### Options

## When Not To Use It
-->

## Further Readings
* [Instruction separation](language.basic-syntax.instruction-separation)

