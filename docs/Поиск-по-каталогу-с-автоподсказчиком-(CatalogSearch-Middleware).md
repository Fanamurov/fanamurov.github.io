Составная часть компонента LarrockCatalog

Позволяет реализовать автоподсказчик для модуля поиска по каталогу.

## Подключение модуля с автоподсказчиком
1. Подключите middleware CatalogSearch для нужных роутов, либо добавьте в app/Http/Kernel.php в секцию 'web': 

    ```php
    Larrock\ComponentCatalog\Middleware\CatalogSearch::class
    ```

2. Вывод шаблона модуля:
    ```php
    @if(file_exists(base_path(). '/vendor/fanamurov/larrock-catalog'))
	    @include('larrock::front.modules.search.catalog-autocomplite')
    @endif
    ```