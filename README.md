[ ![Codeship Status for emartech/guzzle-escher-middleware](https://app.codeship.com/projects/cd815f30-db79-0136-acc2-4a98e051cb94/status?branch=master)](https://app.codeship.com/projects/317747) 
[![GitHub license](https://img.shields.io/github/license/emartech/guzzle-escher-middleware.svg)](https://github.com/emartech/guzzle-escher-middleware/blob/master/LICENSE.md)


# Guzzle Escher Middleware

This authentication middleware add Escher sign functionality to Guzzle Http Client.

## Installation
`composer require emartech/guzzle-escher-middleware`

## Usage
```php
<?php

$credential = new \Guzzle\Http\Middleware\EscherCredential('key', 'secret', 'some/credential/scope');
$escherMiddleware = new \Guzzle\Http\Middleware\EscherMiddleware($credential);

$stack = \GuzzleHttp\HandlerStack::create();

$stack->push($escherMiddleware);

$client   = new \GuzzleHttp\Client(['handler' => $stack]);

// Important: set the auth option to escher to activate the middleware
$response = $client->get('http://www.8points.de', ['auth' => 'escher']);
```