# Optical Character Recognition for PHP

## Description
This library is an abstraction layer for PHP over the Optical Character Recognition engines.

The key feature of the library is that is has no production dependencies. For example, the HTTP-related code is using only [PSR](https://www.php-fig.org/) interfaces and you are free to pick any implementation library and any version of that library thas fits the needs of your project.

## Usage
Add the core package to your project.
~~~
composer require ocr/core
~~~

Add any of the engine packages to you project.
~~~
composer require ocr/some-engine
~~~

Run the recognition process.
~~~php
use OCR\Engine\SomeEngine;
use OCR\Input\File;

$engine = new SomeEngine();
$image = new File('image.png');
$text = $engine->process($image);
~~~
