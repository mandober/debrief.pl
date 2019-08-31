# Laravel

Laravel is a web application framework with expressive, elegant syntax. Laravel is accessible, yet powerful, providing tools needed for large, robust applications.

Laravel attempts to take the pain out of development by easing common tasks used in the majority of web projects, such as:
* Routing
* Dependency injection container
* Multiple back-ends for session and cache storage
* Expressive, intuitive database ORM
* Database agnostic schema migrations
* Robust background job processing
* Real-time event broadcasting

https://laravel.com/
https://laravel.com/docs/5.7/


Laravel Server Requirements
* PHP 7.1.3+
* PHP Extensions:
  * OpenSSL
  * PDO
  * Mbstring
  * Tokenizer
  * XML
  * Ctype
  * JSON
  * BCMath



## Installing Laravel
Laravel utilizes Composer to manage its dependencies.

### Via Laravel Installer
First, download the Laravel installer using Composer:
`composer global require laravel/installer`

Make sure to place composer's system-wide `$HOME/.config/composer/vendor/bin` directory in your `$PATH` so the laravel executable can be located by your system.

Once installed, `laravel new blog` will create a directory named `blog` containing a fresh Laravel installation with all of Laravel's dependencies installed,

### Via Composer Create-Project
Alternatively, you may also install Laravel with `create-project` command in your terminal:
`composer create-project --prefer-dist laravel/laravel blog`

### Local Development Server
If you have PHP installed locally and you would like to use PHP's built-in development server to serve your app use:
`php artisan serve`
This command will start a development server at http://localhost:8000


## Configuration

**Public Directory**
After installing Laravel, you should configure your web server's document / web root to be the  public directory. The index.php in this directory serves as the front controller for all HTTP requests entering your application.

**Configuration Files**
All of the configuration files for the Laravel framework are stored in the config directory. Each option is documented, so feel free to look through the files and get familiar with the options available to you.

**Directory Permissions**
After installing Laravel, you may need to configure some permissions. Directories within the  storage and the bootstrap/cache directories should be writable by your web server or Laravel will not run. If you are using the Homestead virtual machine, these permissions should already be set.

**Application Key**
The next thing you should do after installing Laravel is set your application key to a random string. If you installed Laravel via Composer or the Laravel installer, this key has already been set for you by the php artisan key:generate command.

Typically, this string should be 32 characters long. The key can be set in the .env environment file. If you have not renamed the .env.example file to .env, you should do that now. If the application key is not set, your user sessions and other encrypted data will not be secure!

## Additional Configuration
Laravel needs almost no other configuration out of the box. You are free to get started developing! However, you may wish to review the config/app.php file and its documentation. It contains several options such as timezone and locale that you may wish to change according to your application.

You may also want to configure a few additional components of Laravel, such as:
- Cache
- Database
- Session



## Apache: Pretty URLs

Laravel includes a `public/.htaccess` file that is used to provide URLs without the `index.php` front controller in the path.

Before serving Laravel with Apache, be sure to enable `mod_rewrite` module so the `.htaccess` file will be honored by the server.

If the `.htaccess` file that ships with Laravel does not work with your Apache installation, try this alternative:

```conf
Options +FollowSymLinks -Indexes
RewriteEngine On

RewriteCond %{HTTP:Authorization} .
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^ index.php [L]
```
