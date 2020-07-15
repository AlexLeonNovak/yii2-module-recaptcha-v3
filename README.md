[![Total Downloads](https://img.shields.io/packagist/dt/alexleonnovak/yii2-module-recaptcha-v3.svg?style=flat-square)](https://packagist.org/packages/alexleonnovak/yii2-module-recaptcha-v3) 

Note
----
This is fork from [kekaadrenalin/yii2-module-recaptcha-v3](https://github.com/kekaadrenalin/yii2-module-recaptcha-v3)

Yii2 reCAPTCHA v3
=================
Adds [recaptcha-v3](https://developers.google.com/recaptcha/docs/v3) into yii2 project

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist alexleonnovak/yii2-module-recaptcha-v3 "*"
```

or add

```
"alexleonnovak/yii2-module-recaptcha-v3": "*"
```

to the require section of your `composer.json` file.


Usage
-----

Once the extension is installed, simply use it in your code by  :

add this to your components main.php

```php
'components' => [
    ...
    'reCaptcha3' => [
        'class'      => 'alexleonnovak\recaptcha3\ReCaptcha',
        'site_key'   => 'site_key_###',
        'secret_key' => 'secret_key_###',
    ],

```

and in your model

acceptance_score the minimum score for this request (0.0 - 1.0) or null

```php
public $reCaptcha;
 
public function rules()
{
 	return [
 		...
 		 [['reCaptcha'], \alexleonnovak\recaptcha3\ReCaptchaValidator::className(), 'acceptance_score' => 0]
 	];
}
```

```php
<?= $form->field($model, 'reCaptcha')->widget(\alexleonnovak\recaptcha3\ReCaptchaWidget::class) ?>
```

For tests
---------

When use ```YII_ENV_TEST``` in ```index-test.php``` then disabled recaptcha's validate:
```php
defined('YII_ENV') or define('YII_ENV', 'test');
```