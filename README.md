# Welcome to the Laravel API Authentication Using LARAVEL SANCTUM- wiki!

## Make REST API AUTHENTICATION in LARAVEL 9 USING LARAVEL SANCTUM
Laravel Sanctum provides a featherweight authentication system for SPAs (single page applications), mobile applications, and simple, token based APIs.
Installation Steps
If you are not using LARAVEL 9 you need to install LARAVEL Sanctum Otherwise you can skip the installation step.

### Step 1 
Install via composer
`composer require laravel/sanctum`


### Step 2
Publish the Sanctum Service Provider
`php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"`



### Step 3
Migrate The Database
`php artisan migrate`



## USING SANCTUM IN LARAVEL
User HasApiTokens Trait in App\Models\User
In Order to use Sanctum we need to use HasApiTokens Trait Class in User Model.
User Model should look like.

```php 

<?php

namespace App\Models;

use Illuminate\Contracts\Auth\MustVerifyEmail;
use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Foundation\Auth\User as Authenticatable;
use Illuminate\Notifications\Notifiable;
use Laravel\Sanctum\HasApiTokens;

class User extends Authenticatable
{
    use HasApiTokens, HasFactory, Notifiable;

    /**
     * The attributes that are mass assignable.
     *
     * @var array<int, string>
     */
    protected $fillable = [
        'name',
        'email',
        'password',
    ];

    /**
     * The attributes that should be hidden for serialization.
     *
     * @var array<int, string>
     */
    protected $hidden = [
        'password',
        'remember_token',
    ];

    /**
     * The attributes that should be cast.
     *
     * @var array<string, string>
     */
    protected $casts = [
        'email_verified_at' => 'datetime',
    ];
}
```
