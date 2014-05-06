# Log the activities of your users

[![License](https://poser.pugx.org/spatie/googlesearch/license.png)](https://packagist.org/packages/spatie/googlesearch)

This package provides a very easy to use solution to log the activities of the users of your website or web application. All the activities will be logged in a db-table. Optionally the activities can also be logged against the default Laravel Log Handler.

## Installation

This package can be installed through Composer.
```js
{
    "require": {
		"spatie/activitylog": "dev-master"
	}
}
```

This service provider must be registered.
```php

// app/config/app.php

'providers' => [
    '...',
    'Spatie\Activitylog\ActivitylogServiceProvider'
];
```

You'll also need to publish and run the migration in order to create the db-table.
```
php artisan migrate:publish spatie/activitylog
php artisan migrate 
```

Activitylog also comes with a facade, which provides an easy way to call it.
```php

// app/config/app.php

'aliases' => array(
	...
	'Activity' => 'Spatie\Activitylog\ActivitylogFacade',
)
```

Optionally you can publish the config file of this package.
```
php artisan config:publish spatie/activitylog 
```

The configuration will be written to  ```app/config/packages/spatie/activitylog```. The options provided are self explanatory.


## Usage

```php

/* 
  The log-function takes two parameters:
  	- $text: the activity you wish to log.
  	- $user: optional can be an user id or a user object. 
  	         if not proved the id of Auth::user() will be used
  
*/

Activity::log('Some activity that you wish to log');