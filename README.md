# Thinreports Generator for PHP

[![Latest Stable Version](https://poser.pugx.org/thinreports-php/thinreports-php/version)](https://packagist.org/packages/thinreports-php/thinreports-php)
[![Latest Unstable Version](https://poser.pugx.org/thinreports-php/thinreports-php/v/unstable)](//packagist.org/packages/thinreports-php/thinreports-php)
[![Build Status](https://travis-ci.org/thinreports-php/thinreports-php.svg)](https://travis-ci.org/thinreports-php/thinreports-php)
[![Code Climate](https://codeclimate.com/github/thinreports-php/thinreports-php/badges/gpa.svg)](https://codeclimate.com/github/thinreports-php/thinreports-php)
[![Coverage Status](https://coveralls.io/repos/thinreports-php/thinreports-php/badge.svg?branch=master)](https://coveralls.io/r/thinreports-php/thinreports-php?branch=master)

## About

Thinreports Generator for PHP is an implementation of
the [Thinreports Generator](https://github.com/thinreports/thinreports-generator) in PHP.
It provides easy and simple way for generating a PDF on pure PHP.

### What is Thinreports

Thinreports is an open source report generation tools.
It provides the Thinreports Editor which is a tool for designing a report format,
and the Thinreports Generator for Ruby which is a library for generating a PDF.

Please see the following pages for further details.

  * [Thinreports official site](http://www.thinreports.org)
  * [Thinreports GitHub](https://github.com/thinreports)

## Getting Started

  * [Features](#features)
  * [Quick Start](#quick-start)
  * [Quick Reference](#quick-reference)
  * [Discussion Group on Gitter](https://gitter.im/thinreports-php/thinreports-php?utm_source=share-link&utm_medium=link&utm_campaign=share-link)
  * [Development Community](#development-community)

## Requirements

  * PHP 5.6

## Compatibility with Thinreports

  * Thinreports Editor >= 0.8

## Quick Start

### Step1 Install Thinreports Editor

See the [Official Installation Guide](http://www.thinreports.org/documentation/en/getting-started/installation.html).

### Step2 Install Thinreports Generator for PHP

Put this line in your composer.json:

    "require": {
      "thinreports-php/thinreports-php": "dev-master"
    }

Then `composer install` or `composer update`:

    $ composer install
    -- or --
    $ composer update

### Step3 Create a report format file using the Editor

Follow ["Step1 Creating the layout for the report"](http://www.thinreports.org/documentation/en/getting-started/quickstart.html#toc-2) section in the official doucmentation.

### Step4 Write code for generating a PDF

```php
<?php
// date_default_timezone_set('Asia/Tokyo');

use Thinreports;

$report = new Thinreports\Report('hello_world.tlf');

// 1st page
$page = $report->addPage();
$page->item('world')->setValue('World');
$page->item('thinreports')->setValue('Thinreports');

// 2nd page
$page = $report->addPage();
$page('world')->setValue('PHP');
$page('thinreports')->setValue('Thinreports PHP');

// 3rd page
$page = $report->addPage();
$page('world')->setValue('World')
              ->setStyle('color', '#ff0000');
$page('hello')->hide();

// 4th page
$report->addPage(function ($new_page) {
    $new_page->setItemValues(['world' => 'Japan', 'thinreports' => 'PDF']);
});

$report->generate('hello_world.pdf');
```

**NOTE:**
If you want to render multi-byte characters such as "日本語",
you need to configure the IPAFont to font-family property of the Text-block in the Editor.

## Quick Reference

TODO: Write a reference

## Features

### Implemented

See [Quick Start](#quick-start) and [Quick Reference](#quick-reference)
for currently available features.

### Not Implemented

  * List
  * Multiple Layouts
  * Disabling Hyphenation
  * Font Fallback
  * Permission and Security settings of PDF

### Other Tasks

  * Memory Usage Optimization
    * Disposing raw base64-data after generating a image file
  * Performance Optimization
    * Pre-Converting IPA-Font to AFM from TTF

## Development Community

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/thinreports-php/thinreports-php/dev)

## License

Thinreports PHP is licensed under the MIT-License.
See [LICENSE](https://github.com/thinreports-php/thinreports-php/blob/master/LICENSE) for further details.

### Dependency Library & Resource

#### TCPDF

LGPLv3 / Copyright (c) Nicola Asuni [Tecnick.com](http://www.tecnick.com) LTD

#### IPA Font

[IPA Font License Agreement v1.0](http://ipafont.ipa.go.jp/ipa_font_license_v1.html)

## Copyright

Copyright (c) 2015 [Matsukei Co.,Ltd](http://www.matsukei.co.jp).
