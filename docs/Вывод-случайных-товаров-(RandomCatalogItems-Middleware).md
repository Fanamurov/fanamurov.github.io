Составная часть компонента LarrockCatalog

Позволяет реализовать вывод случайных товаров каталога в виде модуля.

## Подключение модуля случайных товаров
1. Подключите middleware RandomCatalogItems для нужных роутов, либо добавьте в app/Http/Kernel.php в секцию 'web': 

	```php
	Larrock\ComponentCatalog\Middleware\RandomCatalogItems::class
	```

2. Вывод шаблона модуля:
	```php
	@if(isset($RandomCatalogItems))
		@include('larrock::front.modules.list.random_catalog_items', $RandomCatalogItems)
	@endif
	```

##  Конфигурация модуля
Изменение количества выводимых товаров:
Создайте файл конфига /config/larrock.php
```php
<?php

return [
    'catalog' => [
        'RandomCatalogItems' => [
	        'items' => 3,
	        'categories' => [1,2,3, ...],
	        'level' => 3
        ]
    ]
];
```
**items** - количество выводимых товаров. По-умолчанию: 3.
**categories** - разделы для выбора товаров (опционально). По-умолчанию: все опубликованные.
**level** - уровень раздела каталога для выборки товаров (опционально). По-умолчанию: 3.