# Math Captcha Controller

Welcome to the **Math Captcha Controller**! Enhance your form security with our simple yet effective math-based CAPTCHA system. Designed to blend seamlessly into your Laravel projects, this controller ensures your forms are protected from spam while providing a user-friendly experience.

## Features
- **Dynamic CAPTCHA Generation**: Generate random math problems with customizable difficulty.
- **Easy Integration**: Effortlessly add the CAPTCHA to your Blade templates.
- **Session Management**: Securely store CAPTCHA data in the session.
- **Customizable Input and Script**: Personalize the CAPTCHA input field and script behavior.
- **Validation Logic**: Ensure user input matches the CAPTCHA solution with robust

#Quick Start

## Add Captcha Refresh Route
Add this route to refresh the captcha:

```php
// In App\Http\Controllers\MathCaptchaController
Route::get('get-captcha', [MathCaptchaController::class, 'resetCaptcha'])->name('get.captcha');
```

## Use Captcha Input in Blade
To show the captcha input in a Blade template:

```php
{!! \App\Http\Controllers\MathCaptchaController::input() !!}
```

### Customizing Captcha Input
You can customize the captcha input by passing parameters:

```php
{!! \App\Http\Controllers\MathCaptchaController::input('captcha_field', 'target_element', 'custom_classes') !!}
```
- `captcha_field`: The name of the captcha input field (default is "captcha").
- `target_element`: The parent element for the captcha input (optional).
- `custom_classes`: Any additional classes for the captcha input field (optional).

## Use Captcha Script in Blade
To include the captcha script in a Blade template:

```php
{!! \App\Http\Controllers\MathCaptchaController::getScript() !!}
```

### Customizing Captcha Script
You can customize the captcha script by specifying the selector:

```php
{!! \App\Http\Controllers\MathCaptchaController::getScript('#custom_selector') !!}
```
- `#custom_selector`: The jQuery selector where the new HTML code with input will be loaded (default is `#captcha-wrapper`).

## Controller Validation Logic
To validate the captcha in your controller:

```php
$cvalidate = MathCaptchaController::validate($request);

if ($cvalidate !== true) {
    // Your logic here if captcha is invalid
}
```

## Customization Options (in MathCaptchaController.php)

### Configurable Number Range and Operators
Customize the number range and operators directly in the controller:

```php
// Modify these variables in the MathCaptchaController
public static $min = 1; // Minimum number
public static $max = 20; // Maximum number
public static $operators = ['+', '-']; // Operators list
```

### Custom Error Messages
Set custom error messages for captcha validation:

```php
$cvalidate = MathCaptchaController::validate($request, 'captcha', 'Incorrect answer, try again.');

if ($cvalidate !== true) {
    // Your logic here if captcha is invalid
}
```
