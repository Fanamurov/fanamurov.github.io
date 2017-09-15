## Список компонентов для генерации карты сайта
Список находится в файле **config/larrock-sitemap.xml** и представляет собой:
```php
<?php

$components = [];

if(file_exists(base_path(). '/vendor/fanamurov/larrock-pages')){
    $components[] = new \Larrock\ComponentPages\PageComponent();
}
...

return [
    'components' => $components
];
```

Каждый элемент массива должен быть ссылкой на файл компонента внутри которого описан метод **createSitemap()**:
```php
public function createSitemap()
{
    return $this->getModel()->whereActive(1)->get();
}
```
возвращающий список элементов входящих в карту сайта.

## Генерация карты сайта:
Перейдите по ссылке: http://yoursite.com/sitemap.xml