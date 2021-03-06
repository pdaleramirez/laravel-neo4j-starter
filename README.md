# LaravelNeo4jStarter

This is a starter package for laravel that uses the neo4j database. 
Authentication, Registration and Password Resets are also implemented on this package.

## Quick Reference

 - [Installation](#installation)
 - [Configuration](#configuration)

## Installation

Add the package to your `composer.json` and run `composer update`.

### Laravel 5

#### 5.3 - 5.4

```json
{
    "require": {
        "pdaleramirez/laravel-neo4j-starter": "dev-master"
    }
}
```
Add the service provider in `app/config/app.php`:

```php
pdaleramirez\LaravelNeo4jStarter\Providers\Neo4jServiceProvider::class,
```
The service provider will register all the required classes for Laravel Neo4j Starter package.
  
Add the required facades in `app/config/app.php`:

```php
'Neo4jQuery' 	  => pdaleramirez\LaravelNeo4jStarter\Facades\Neo4jQueryFacade::class
```

## Configuration

### Connection

Open environment-based configuration '.env' file then define your configuration.

```
NEO4J_HOST=localhost
NEO4J_PORT=7474
NEO4J_USERNAME=neo4j
NEO4J_PASSWORD=neo4j
```

On your application root open config/auth.php and change the providers values with the one below.

```
    'providers' => [
        'users' => [
            'driver' => 'neo4jauth',
            'model' => pdaleramirez\LaravelNeo4jStarter\Models\User::class,
        ],
    ],
```


## Password Resets

Open your app/Http/Controllers/Auth/ForgotPasswordController.php and app/Http/Controllers/Auth/RegisterController.php 
file and this method to the class.

```php
public function broker()
{
	return \App::make('auth.password.neo4j');
}
```
