**Внимание: компонент поставляется вместе с ядром (larrock-core), дополнительная установка не требуется.**

#### Depends
- fanamurov/larrock-core

## INSTALL

1. Install larrock-core
2. Install larrock-contacts
  ```sh
  composer require fanamurov/larrock-contacts
  ```

3. Add the ServiceProvider to the providers array in app/config/app.php
  ```
  //LARROCK COMPONENT Contacts DEPENDS
  \Larrock\ComponentContacts\LarrockComponentContactsServiceProvider::class
  ```

4. Publish views, migrations etc.
  ```sh
  $ php artisan vendor:publish
  ```
  Or
  ```sh
  $ php artisan vendor:publish --provider="Larrock\ComponentContacts\LarrockComponentContactsServiceProvider"
  ```
  
5. Run migrations
  ```sh
  $ php artisan migrate
  ```