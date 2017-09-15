#### Depends
- fanamurov/larrock-core
- fanamurov/larrock-category

## INSTALL

1. Install larrock-core, larrock-category
2. Install larrock-feed
  ```sh
  composer require fanamurov/larrock-feed
  ```

3. Add the ServiceProvider to the providers array in app/config/app.php
  ```
  //LARROCK COMPONENT FEED DEPENDS
  \Larrock\ComponentFeed\LarrockComponentFeedServiceProvider::class
  ```

4. Publish views, migrations etc.
  ```sh
  $ php artisan vendor:publish
  ```
  Or
  ```sh
  $ php artisan vendor:publish --provider="Larrock\ComponentFeed\LarrockComponentFeedServiceProvider"
  ```
  
5. Run migrations
  ```sh
  $ php artisan migrate
  ```

## START
http://yousite/admin/feed