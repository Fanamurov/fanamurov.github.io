# First steps (первые шаги) - routes
Переопределение главной страницы и внедрение других собственных роутов

**Файл /routes/web.php**

   1. Добавьте секцию для подключения middleware компонентов
	
```php
$middlewares = ['web', 'GetSeo'];
if(file_exists(base_path(). '/vendor/fanamurov/larrock-menu')){
    $middlewares[] = 'AddMenuFront';
}
if(file_exists(base_path(). '/vendor/fanamurov/larrock-blocks')){
    $middlewares[] = 'AddBlocksTemplate';
}
if(file_exists(base_path(). '/vendor/fanamurov/larrock-discount')){
    $middlewares[] = 'DiscountsShare';
}
```

   2. Переназначьте главный роут (для примера указан экшен вывода главных разделов каталога из компонента LarrockCatalog)

```php
Route::group(['middleware' => $middlewares], function(){
    Route::get('/', '\Larrock\ComponentCatalog\CatalogController@getCategoryRoot');
});
```