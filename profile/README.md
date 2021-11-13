# Optical Character Recognition for PHP

## Description
This library is an abstraction layer for PHP over the Optical Character Recognition engines.

The key feature of the library is that is has no production dependencies. For example, the HTTP-related code is using only [PSR](https://www.php-fig.org/) interfaces and you are free to pick any implementation library and any version of that library thas fits the needs of your project.

## Installation
Add the core package to your project.
~~~
composer require ocr/core
~~~

Add any of the engine packages to you project.
~~~
composer require ocr/some-engine
~~~

## Usage – bird's eye view
~~~php
use OCR\Engine\SomeEngine;
use OCR\Input\File;

$engine = new SomeEngine();
$image = new File('image.png');
$text = $engine->process($image);
~~~

## Usage – complete example
This example uses the HTTP API provided by [https://ocr.space](https://ocr.space/). You will have to acquire an API key to use the following example. 

Additionally install any implementation of `psr/http-client`, `psr/http-factory` and `psr/http-factory`. For example, `guzzlehttp/guzzle` and `guzzlehttp/psr7`.

~~~php
use GuzzleHttp\Client;
use GuzzleHttp\Psr7\HttpFactory;
use OCR\Engine\OcrSpaceEngine;
use OCR\Input\File;
use OCR\Utility\Http\Request\Multipart\GuzzleMultipartFormFactory;

$httpClient = new Client();
$requestFactory = new HttpFactory();
$formFactory = new GuzzleMultipartFormFactory();
$engine = new OcrSpaceEngine($httpClient, $requestFactory, $formFactory, 'api-key');

$image = new File('input.jpeg');

$text = $engine->process($image);
~~~
