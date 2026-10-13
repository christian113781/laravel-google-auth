# Laravel Google Auth

A simple Laravel project demonstrating **Sign in with Google** using **Laravel Socialite** and **Google OAuth 2.0**.

This project allows users to authenticate with their Google account without requiring Firebase.

## Features

- Sign in with Google
- Google OAuth 2.0 authentication
- Laravel Socialite integration
- Automatically create new users
- Login existing users using their Google account
- Store Google ID and profile information
- Laravel session authentication
- MySQL database support

## Tech Stack

- Laravel
- Laravel Socialite
- Google OAuth 2.0
- PHP
- MySQL
- Tailwind CSS

## Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/laravel-google-auth.git
```

Go to the project directory:

```bash
cd laravel-google-auth
```

Install PHP dependencies:

```bash
composer install
```

Install frontend dependencies:

```bash
npm install
```

Create your environment file:

```bash
cp .env.example .env
```

Generate the application key:

```bash
php artisan key:generate
```

Configure your database in `.env`:

```env
DB_DATABASE=laravel_google_auth
DB_USERNAME=root
DB_PASSWORD=
```

Run the migrations:

```bash
php artisan migrate
```

## Install Laravel Socialite

```bash
composer require laravel/socialite
```

## Google OAuth Setup

Create OAuth credentials in the **Google Cloud Console**.

Create an **OAuth 2.0 Client ID** and add this callback URL:

```text
http://localhost:8000/auth/google/callback
```

Then add your Google credentials to `.env`:

```env
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GOOGLE_REDIRECT_URI=http://localhost:8000/auth/google/callback
```

> Never commit your Google Client Secret or `.env` file to GitHub.

## Socialite Configuration

Add the Google configuration to:

```text
config/services.php
```

```php
'google' => [
    'client_id' => env('GOOGLE_CLIENT_ID'),
    'client_secret' => env('GOOGLE_CLIENT_SECRET'),
    'redirect' => env('GOOGLE_REDIRECT_URI'),
],
```

## Run the Project

Start the Laravel development server:

```bash
php artisan serve
```

Run Vite:

```bash
npm run dev
```

Open:

```text
http://localhost:8000
```

Click **Continue with Google** to authenticate using your Google account.

## Authentication Flow

```text
User
 ↓
Continue with Google
 ↓
Google OAuth
 ↓
Laravel Socialite
 ↓
Google Callback
 ↓
Find or Create User
 ↓
Laravel Authentication
 ↓
Dashboard
```

## Purpose

This repository is a simple reference implementation for developers who want to integrate **Google authentication into a Laravel application without Firebase**.

It can also be used as a starting point for adding other OAuth providers such as GitHub or Facebook.

## License

This project is open-source and available under the MIT License.
