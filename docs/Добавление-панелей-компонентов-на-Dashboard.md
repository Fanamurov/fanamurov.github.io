Любой компонент можно вывести на главную страницу админки (dashboard). Метод можно использовать для вывода быстрых ссылок на создание новых материалов, вывода статистики или любых других данных.

## Вывод панели
1. Создайте и опишите в компоненте (например в BlocksComponent.php) функцию toDashboard
	```php
	public function toDashboard()
	{
	    return view('larrock::admin.dashboard.blocks', ['component' => LarrockBlocks::getConfig()]);
	}
	```

2. Создайте файл шаблона вывода панели (например: admin/dashboard/blocks.blade.php)
	```
	<div id="dashboard-blocks" class="dashboard-item uk-width-small-1-2 uk-width-medium-1-4">
	    <div class="uk-panel uk-alert">
	        <p class="uk-h3"><a href="/admin/{{ $component->name }}">{{ $component->title }}</a></p>
	        <a href="/admin/blocks/create" class="uk-button uk-button-primary">Создать блок</a>
	    </div>
	</div>
	```

3. В файле конфига config/larrock-to-dashboard.php пропишите ссылку на подключение компонента:
	```php
	<?php
	
	$components = [];
	
	if(file_exists(base_path(). '/vendor/fanamurov/larrock-blocks')){
	    $components[] = new \Larrock\ComponentBlocks\BlocksComponent();
	}
	
	return [
	    'components' => $components
	];
	```

## Изменение вывода панелей по-умолчанию
Вы всегда можете изменить шаблон вывода через редактирование самого шаблона /views/vendor/larrock/admin/dashboard/НазваниеКомпонента.blade.php. Либо полностью изменить поведение панели [переназначив сам компонент](https://github.com/Fanamurov/larrock-core/wiki/%D0%9F%D0%B5%D1%80%D0%B5%D0%BD%D0%B0%D0%B7%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B5%D0%BA-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-%28%D0%B8%D0%B7%D0%BC%D0%B5%D0%BD%D0%B5%D0%BD%D0%B8%D0%B5-Component-%D0%B8-Model%29).