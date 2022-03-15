# Clear Chace Laravel



#### Check Laravel Version

```
php artisan --version
vim ./vendor/laravel/framework/src/Illuminate/Foundation/Application.php
```

#### Clear Application Cache

```
php artisan cache:clear
```

#### Clear Route Cache

```
php artisan route:clear
```

#### Clear Configuration Cache

```
php artisan config:clear
```

#### Clear Compiled Views Cache

```
php artisan view:clear
```

```
Route::get('/clear-cache', function() {
    Artisan::call('cache:clear');
    return "Cache is cleared";
});
```
