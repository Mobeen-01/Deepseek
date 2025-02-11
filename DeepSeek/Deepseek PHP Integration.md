
## Alternative: Using DeepSeek PHP Client Directly

### Step 1: Clone the Repository
Clone the DeepSeek PHP Client repository:

```bash
git clone https://github.com/deepseek-php/deepseek-php-client
```

Navigate to the project directory:

```bash
cd deepseek-php-client
```

### Step 2: Install Dependencies
Require the package via Composer:

```bash
composer require deepseek-php/deepseek-php-client
```

If you encounter errors, try running:

```bash
composer install
composer update
```

### Step 3: Create and Test a Simple Script
Download the following file to test the integration:

[📥 Download test.php](test.php)

Create a new file `test.php` and add the following code:

```php
<?php

require 'vendor/autoload.php'; // Ensure Composer autoload is included

use DeepSeek\DeepSeekClient;

// Replace 'your-api-key' with your actual API key
$client = DeepSeekClient::build('sk-e35dff1c965941368af04ec411451cef');

$response = $client
    ->query('Explain quantum computing in simple terms') // Change the message as needed
    ->run();

echo "Response from DeepSeek: " . $response;
```

## Reference
All integration steps were followed using the official DeepSeek Laravel wrapper documentation:
[DeepSeek Laravel GitHub Repository](https://github.com/deepseek-php/deepseek-laravel/blob/master/README.md)

DeepSeek Laravel provides the best Laravel wrapper for the [DeepSeek PHP Client](https://github.com/deepseek-php/deepseek-php-client), enabling seamless integration with the [DeepSeek AI API](https://www.deepseek.com/).
