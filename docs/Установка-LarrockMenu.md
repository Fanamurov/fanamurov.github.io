**Внимание: компонент поставляется вместе с ядром (larrock-core), дополнительная установка не требуется.**

#### Depends
- fanamurov/larrock-core

## INSTALL

1. Install larrock-core
2. Install larrock-menu
  ```sh
  composer require fanamurov/larrock-menu
  ```

3. Add the ServiceProvider to the providers array in app/config/app.php
  ```
  //LARROCK COMPONENT Menu DEPENDS
  \Larrock\ComponentPages\LarrockComponentPagesServiceProvider::class
  ```

4. Publish views, migrations etc.
  ```sh
  $ php artisan vendor:publish
  ```
  Or
  ```sh
  $ php artisan vendor:publish --provider="Larrock\ComponentMenu\LarrockComponentMenuServiceProvider"
  ```
  
5. Run migrations
  ```sh
  $ php artisan migrate
  ```

## START
http://yousite/admin/menu