# Integrating DeepSeek with Laravel

## Step 1: Create a New Laravel Project
Run the following command to create a new Laravel project:

```bash
composer create-project --prefer-dist laravel/laravel deepseek-laravel-demo
```

Navigate to the project directory:

```bash
cd deepseek-laravel-demo
```

## Step 2: Install DeepSeek Package
You can install the package via Composer:

```bash
composer require deepseek-php/deepseek-laravel
```

## Step 3: Publish Configuration File
Run the following command to publish the DeepSeek configuration file:

```bash
php artisan vendor:publish --tag=deepseek
```

## Step 4: Add API Key to `.env` File
Open your `.env` file and add the following line:

```env
DEEPSEEK_API_KEY="your_api_key"
```

To get an API key, create a new one from the following link:
[DeepSeek API Keys](https://platform.deepseek.com/api_keys)

## Step 5: Test DeepSeek Integration
Open `routes/web.php` and add the following code to test the integration:

```php
<?php

use Illuminate\Support\Facades\Route;
use DeepSeek\DeepSeekClient;
use GuzzleHttp\Client;
use DeepSeek\Enums\Models;

Route::get('/', function () {
    // Replace 'your-api-key' with your actual API key
    $client = DeepSeekClient::build(env('DEEPSEEK_API_KEY'));

    $response = $client
        ->query('Explain quantum computing in simple terms') // Change the message as needed
        ->run();

    dd("Response from DeepSeek: " . $response);
});
```

## Reference
All integration steps were followed using the official DeepSeek Laravel wrapper documentation:
[DeepSeek Laravel GitHub Repository](https://github.com/deepseek-php/deepseek-laravel/blob/master/README.md)

DeepSeek Laravel provides the best Laravel wrapper for the [DeepSeek PHP Client](https://github.com/deepseek-php/deepseek-php-client), enabling seamless integration with the [DeepSeek AI API](https://www.deepseek.com/).
