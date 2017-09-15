**Внимание: компонент поставляется вместе с ядром (larrock-core), дополнительная установка не требуется.**

#### Depends
- fanamurov/larrock-blocks

## INSTALL

1. Install larrock-core
2. Install larrock-blocks
  ```sh
  composer require fanamurov/larrock-blocks
  ```

3. Add the ServiceProvider to the providers array in app/config/app.php
  ```
  //LARROCK COMPONENT BLOCKS DEPENDS
  \Larrock\ComponentBlocks\LarrockComponentBlocksServiceProvider::class
  ```

4. Publish views, migrations etc.
  ```sh
  $ php artisan vendor:publish
  ```
  Or
  ```sh
  $ php artisan vendor:publish --provider="Larrock\ComponentBlocks\LarrockComponentBlocksServiceProvider"
  ```
  
5. Run migrations
  ```sh
  $ php artisan migrate
  ```

## START
http://yousite/admin/blocks