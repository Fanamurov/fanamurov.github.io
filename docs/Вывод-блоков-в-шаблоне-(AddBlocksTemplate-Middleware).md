Составная часть компонента LarrockBlocks

Редактирование пунктов меню: /admin/blocks

Для вывода компонентов меню используется Middleware AddBlocksTemplate (/vendor/fanamurov/larrock-blocks/src/Middleware/AddBlocksTemplate.php).

В шаблоне вывода шарятся переменные с контентом (коллекция данных) блока по его url. Например: {{ $block_main }}. Для вывода блока удобнее всего использовать:

    @if(isset($block_main))
        @include('larrock::front.modules.html.text', ['data' => $block_main])
    @endif

в таком случае блок будет обрамлен своим контейнером и получит быструю ссылку на редактирование в админку.