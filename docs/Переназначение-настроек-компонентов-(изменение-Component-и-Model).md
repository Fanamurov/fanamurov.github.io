Конфигурацию любого компонента можно изменить (название, имя таблицы, используемые поля, используемую модель) или дополнить своими классами.

1.Создайте файл **config/larrock.php** со следующим содержанием:


	```php
	<?php

	return [
	    'components' => [
	        'краткое название компонента' => Класс компонента
	    ],

	    'models' => [
	  'краткое название компонента' => Класс модели компонента
	    ]
	];
	```

2.Создайте файл с новым конфигом компонента, например в папке app/Components, с наследованием от базового Components компонента:

```php
class НазваниеКомпонентаComponent extends \Larrock\ComponentНазваниеКомпонента\НазваниеКомпонентаComponent 
```

3.По аналогии можете создать класс Модели

Переназначьте конструктор и добавьте свои изменения:
```php
public function __construct()
{
    parent::__construct();
    //Ваши классы или переназначенные атрибуты
}
```

## Например (переназначение конфига компонента LarrockFeed):

### Добавим в компонент Feed новое поле status

1.Добавляем в таблицу БД компонента feed новое поле status

```sql
ALTER TABLE `feed`
ADD `status` varchar(191) COLLATE 'utf8mb4_unicode_ci' NOT NULL AFTER `active`;
```

2.Создаем **app/Components/FeedComponent.php**
```php
<?php

namespace App\Components;

use Larrock\Core\Helpers\FormBuilder\FormSelect;

class FeedComponent extends \Larrock\ComponentFeed\FeedComponent
{
    public function __construct()
    {
        parent::__construct();
        $this->addAdditionalRows();
    }

    protected function addAdditionalRows()
    {
        $row = new FormSelect('status', 'Статус вакансии');
        $this->rows['status'] = $row->setOptions(['Свободна', 'Закрыта'])->setDefaultValue('Свободна')->setFillable();

        return $this;
    }
}
```
	
Примечание:
Метод setFillable() обязателен, если вы хотите сделать автоматическое сохранение данных поля в таблицу БД компонента.


3.Прописываем новый конфиг компонента в файле **config/larrock.php**
```php
<?php

use App\Components\FeedComponent;
use App\Models\Feed;

return [
    'components' => [
        'feed' => FeedComponent::class
    ],
    
    'models' => [
        'feed' => Feed::class
    ]
];
```