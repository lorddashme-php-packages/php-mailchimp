# PHP MailChimp

A PHP package wrapper for MailChimp API.

[![Latest Stable Version](https://img.shields.io/packagist/v/LordDashMe/php-mailchimp.svg?style=flat-square)](https://packagist.org/packages/LordDashMe/php-mailchimp) [![Minimum PHP Version](https://img.shields.io/badge/php-%3E%3D%205.6-8892BF.svg?style=flat-square)](https://php.net/) [![Build Status](https://img.shields.io/travis/LordDashMe/php-mailchimp/master.svg?style=flat-square)](https://travis-ci.org/LordDashMe/php-mailchimp) [![Coverage Status](https://img.shields.io/coveralls/LordDashMe/php-mailchimp/master.svg?style=flat-square)](https://coveralls.io/github/LordDashMe/php-mailchimp?branch=master)

## Requirement(s)

- PHP version from 5.6.* up to latest.

## Install

- It is advice to install the package via Composer. Use the command below to install the package:

```txt
composer require lorddashme/php-mailchimp
```

## Usage

- Below are the available functions:

| Function | Description |
| -------- | ----------- |
| <img width=200/>  |<img width=200/> |
| ```post(route, body);``` | To request in the MailChimp API service using POST method. |
| ```get(route);``` | To request in the MailChimp API service using GET method. |
| ```patch(route, body);``` | To request in the MailChimp API service using PATCH method. |
| ```delete(route);``` | To request in the MailChimp API service using DELETE method. |
| ```action(route);``` | To request in the MailChimp API service using the custom ACTION. |
| ```getRequest();``` | To check the current request details. Can be use for debugging purposes. |
| ```getRespose();``` | To get the current response from the MailChimp API service. <br> Response: ```{"response_body": {...}", "header": {"response_http_code": ...}}``` |

- The basic usage of the package:

```php
<?php

include __DIR__  . '/vendor/autoload.php';

use LordDashMe\MailChimp\MailChimp;

$mailchimp = new MailChimp('abcde12345...');

$mailchimp->post("list/{$listId}/members", function ($requestBody) {
    $requestBody->email_address = 'sample_email@mailchimp.com';
    return $requestBody;
});

// To investigate the current request details..
$mailchimp->getRequest();

// To get the response from the MailChimp API service.
// Sample Response: {"response_body": {...}", "header": {"response_http_code": ...}}
$response = $mailchimp->getResponse();
```

- Also can be done by the below implementation:

```php
<?php

include __DIR__  . '/vendor/autoload.php';

use LordDashMe\MailChimp\Facade\MailChimp;

MailChimp::init('abcde12345...');

MailChimp::post("list/{$listId}/members", array(
    'email_address' => 'sample_email@mailchimp.com'
));

// To investigate the current request details..
MailChimp::getRequest();

// To get the response from the MailChimp API service.
// Sample Response: {"response_body": {...}", "header": {"response_http_code": ...}}
$response = MailChimp::getResponse();
```

## License

This package is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
