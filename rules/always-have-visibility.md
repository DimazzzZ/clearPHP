<!-- Хорошая практика -->
# Всегда указывайте видимость

Из соображений совместимости PHP позволяет определять методы и свойства без указаниях их видимости: `public`, 
`protected`, `private`. По умолчанию методы и свойства определены как публичные (`public`), что позволяет обращаться к 
ним без каких либо ограничений.

Один из подходов программирования - всегда ставить видимость `private`, после чего уже можно ослаблять ограничение, 
если данный ресурс требуется в дочернем классе или за его пределеами.

Это один из основных принципов объектно-ориентированного программирования: инкапсуляция. Он должен быть использован для 
разделения как можно большего количества "внутренностей" объекта извне, ограничивая их влияние до выбранных методов или 
свойств.

Рекомендуется всегда устанавливать ограниченную видимость насколько это возможно.

## Подробнее о правиле

This rule is aimed at avoiding omitting visibility for properties and methods.

The following patterns are considered warnings:

```php
<?php

abstract class x {
	static $staticProperty;
	var $varProperty;

	function defautVisibilityMethod() {}
	static function defautVisibilityStaticMethod() {}
	final function defautVisibilityFinalMethod() {}
	abstract function defautVisibilityAbstractMethod();
	
}

?>
```

The following patterns are not considered warnings:

```php
<?php

abstract class x {
	static protected $staticProperty;
	public $varProperty;

	public function defautVisibilityMethod() {}
	static protected function defautVisibilityStaticMethod() {}
	final private function defautVisibilityFinalMethod() {}
	abstract public function defautVisibilityAbstractMethod();
	
}

?>
```

<!--
### Options

## When Not To Use It

## Further Readings
-->

