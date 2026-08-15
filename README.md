# Adlynk

Adlynk is a Laravel 10 web application foundation configured with a Vite-powered frontend, MySQL database support, authentication/session tooling, Laravel Sanctum, Laravel Socialite, and audit logging.

> **Note:** This README is based on the project configuration files provided with the project. The uploaded source set does not expose the full application feature set, controllers, routes, models, or UI, so feature descriptions are limited to what can be verified from the available files.

## Tech Stack

- **Backend:** PHP 8.1+, Laravel 10.10
- **Frontend tooling:** Vite 5
- **Database:** MySQL
- **Authentication/API:** Laravel Sanctum
- **Social authentication:** Laravel Socialite
- **HTTP client:** Guzzle
- **Auditing:** OwenIt Laravel Auditing
- **Testing:** PHPUnit 10
- **Development tools:** Laravel Pint, Laravel Sail, Laravel Tinker
- **JavaScript dependency:** Axios
- **Build integration:** Laravel Vite Plugin

The Composer configuration confirms PHP `^8.1`, Laravel `^10.10`, Sanctum, Socialite, Tinker, Guzzle, and Laravel Auditing as project dependencies. 

## Project Highlights

- Laravel 10 application architecture
- MySQL database configuration
- Vite-based frontend asset development and production builds
- Google OAuth configuration through Laravel Socialite
- Facebook OAuth configuration through Laravel Socialite
- API authentication support through Sanctum
- Application activity/audit logging support
- PHPUnit unit and feature testing structure
- Environment-based application configuration

## Requirements

Before running the project, install:

- PHP 8.1 or newer
- Composer
- Node.js and npm
- MySQL
- Git

Recommended PHP extensions should match the requirements of your Laravel 10 environment.

## Installation

### 1. Clone the repository

```bash
git clone <YOUR_REPOSITORY_URL>
cd <PROJECT_DIRECTORY>
```

### 2. Install PHP dependencies

```bash
composer install
```

### 3. Install frontend dependencies

```bash
npm install
```

### 4. Configure environment

Create your local environment file:

```bash
cp .env.example .env
```

On Windows PowerShell:

```powershell
Copy-Item .env.example .env
```

Generate the Laravel application key:

```bash
php artisan key:generate
```

### 5. Configure the database

Update the database values in `.env`:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=myad
DB_USERNAME=root
DB_PASSWORD=
```

Then run migrations:

```bash
php artisan migrate
```

If the project contains seeders that are required for local development:

```bash
php artisan db:seed
```

### 6. Start the development environment

Run the Laravel server:

```bash
php artisan serve
```

In another terminal, start Vite:

```bash
npm run dev
```

The application can then be opened at the URL reported by `php artisan serve`.

## Frontend Build

For development:

```bash
npm run dev
```

For a production asset build:

```bash
npm run build
```

The Vite configuration uses:

```text
resources/css/app.css
resources/js/app.js
```

as its frontend entry points.

## Authentication

The project includes Laravel Socialite and environment configuration for:

- Google OAuth
- Facebook OAuth

Configure the corresponding credentials in `.env` before enabling social login in a local or production environment.

Example configuration structure:

```env
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GOOGLE_REDIRECT=https://your-domain.com/auth/google/callback

FB_CLIENT_ID=your_facebook_client_id
FB_CLIENT_SECRET=your_facebook_client_secret
FB_REDIRECT=https://your-domain.com/auth/facebook/callback
```

**Never commit real OAuth credentials, API keys, passwords, or `.env` files to GitHub.**

## Testing

The PHPUnit configuration includes separate test suites for:

- `tests/Unit`
- `tests/Feature`

Run the complete test suite with:

```bash
php artisan test
```

Or directly with PHPUnit:

```bash
vendor/bin/phpunit
```

## Code Quality

Laravel Pint is included as a development dependency.

Run:

```bash
./vendor/bin/pint
```

On Windows:

```powershell
vendor\bin\pint
```

## Useful Artisan Commands

```bash
php artisan about
php artisan route:list
php artisan migrate
php artisan migrate:fresh
php artisan db:seed
php artisan config:clear
php artisan cache:clear
php artisan optimize:clear
php artisan storage:link
```

Use destructive commands such as `migrate:fresh` only on development/testing databases.

## Project Structure

Typical Laravel application structure:

```text
Adlynk/
├── app/
│   ├── Console/
│   ├── Exceptions/
│   ├── Http/
│   ├── Models/
│   └── Providers/
├── bootstrap/
├── config/
├── database/
│   ├── factories/
│   ├── migrations/
│   └── seeders/
├── public/
├── resources/
│   ├── css/
│   └── js/
├── routes/
├── storage/
├── tests/
│   ├── Feature/
│   └── Unit/
├── .env.example
├── artisan
├── composer.json
├── package.json
├── phpunit.xml
└── vite.config.js
```

## Environment & Security

The application uses environment variables for database, mail, AWS, Pusher, frontend, and social-login configuration.

For security:

1. Keep `.env` private.
2. Use `.env.example` only for placeholder configuration.
3. Rotate credentials if real secrets have ever been exposed publicly.
4. Set `APP_DEBUG=false` in production.
5. Use HTTPS in production.
6. Use a strong production database password.
7. Do not commit OAuth client secrets or other credentials.

## Production Checklist

Before deploying:

- [ ] Set `APP_ENV=production`
- [ ] Set `APP_DEBUG=false`
- [ ] Configure the production `APP_URL`
- [ ] Configure a production MySQL database
- [ ] Configure production OAuth callback URLs
- [ ] Configure production mail
- [ ] Run `composer install --no-dev --optimize-autoloader`
- [ ] Run `npm run build`
- [ ] Run database migrations
- [ ] Clear and rebuild Laravel caches
- [ ] Configure the web server and PHP-FPM
- [ ] Enable HTTPS
- [ ] Verify file/storage permissions
- [ ] Run the test suite

## Available Scripts

### Composer

```bash
composer install
composer update
php artisan test
```

### NPM

```bash
npm install
npm run dev
npm run build
```

## License

The application is built on Laravel, which is distributed under the MIT license. The project's own license should be confirmed before publishing or redistributing application-specific code.

## Credits

Built with:

- Laravel
- PHP
- Vite
- MySQL
- Laravel Sanctum
- Laravel Socialite
- PHPUnit

## Author

**Adlynk Project**

For repository-specific questions, issues, or contributions, use the project's GitHub repository issue tracker and contribution guidelines.
