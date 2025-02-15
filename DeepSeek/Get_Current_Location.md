# Location Finder

## Overview
This project provides methods to retrieve the current user's public IP address, country, city, and other geolocation details using different APIs. 

## Methods
### 1. Using `checkip.amazonaws.com` & `ip-api.com`
**Code:**
```php
function getPublicIP() {
    $ch = curl_init('https://checkip.amazonaws.com');
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
    $ip = curl_exec($ch);
    curl_close($ch);
    return trim($ip);
}

$user_ip = getPublicIP();
$geoData = file_get_contents("http://ip-api.com/json/$user_ip");
$geo = json_decode($geoData, true);
$country = $geo["country"] ?? 'Unknown';
$city = $geo["city"] ?? 'Unknown';

dd($user_ip, $geo, $country, $city);
```
**Output:**
```json
"119.152.22.90"
{
  "status": "success",
  "country": "Pakistan",
  "city": "Lahore",
  "lat": 31.5204,
  "lon": 74.3587
}
"Pakistan"
"Lahore"
```
**Pros:**
- Free to use
- Fast response time
**Cons:**
- City detection might not be accurate

---
### 2. Using `api64.ipify.org` & `ip-api.com`
**Code:**
```php
$user_ip = file_get_contents('https://api64.ipify.org');
$geoData = file_get_contents("http://ip-api.com/json/$user_ip");
$geo = json_decode($geoData, true);
$country = $geo["country"] ?? 'Unknown';
$city = $geo["city"] ?? 'Unknown';

dd($user_ip, $geo, $country, $city);
```
**Output:**
```json
"119.152.22.90"
{
  "status": "success",
  "country": "Pakistan",
  "city": "Lahore",
  "lat": 31.5204,
  "lon": 74.3587
}
"Pakistan"
"Lahore"
```
**Pros:**
- Free to use
- Fast response time
**Cons:**
- City detection might not be accurate

---
### 3. Using `ipgeolocation.io` (Paid)
**Steps:**
1. Sign up at [ipgeolocation.io](https://app.ipgeolocation.io/signup).
2. Get an API key from the documentation.
3. Use the following code:

**Code:**
```php
function getPublicIP() {
    $ch = curl_init('https://checkip.amazonaws.com');
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
    $ip = curl_exec($ch);
    curl_close($ch);
    return trim($ip);
}

$user_ip = getPublicIP();
$apiKey = 'your_api_key_here'; // Replace with your API key
$geoData = file_get_contents("https://api.ipgeolocation.io/ipgeo?apiKey=$apiKey&ip=$user_ip");
$geo = json_decode($geoData, true);
$country = $geo["country_name"] ?? 'Unknown';
$city = $geo["city"] ?? 'Unknown';

dd($user_ip, $geo, $country, $city);
```
**Output:**
```json
"119.152.22.90"
{
  "country_name": "Pakistan",
  "city": "Rawalpindi",
  "latitude": "33.56511",
  "longitude": "73.01691"
}
"Pakistan"
"Rawalpindi"
```
**Pros:**
- Accurate city detection
- Provides more detailed location data
**Cons:**
- Paid service
- Slower response time

## Conclusion
- **Method 1 & 2** are free and fast but may provide inaccurate city detection.
- **Method 3** is paid but provides accurate and detailed location data.
- Choose based on your needs: speed vs accuracy.
