# Akeneo PIM extension starter

[Experimental] Starter kit to quickly setup your own Akeneo PIM Extension

![](https://img.shields.io/badge/PIM%20community-1.3-red.svg)
![](https://img.shields.io/badge/PIM%20community-1.4-red.svg)
![](https://img.shields.io/badge/PIM%20community-1.5-green.svg)

[![Build Status](https://travis-ci.org/akeneo-labs/ExtensionStarter.svg?branch=master)](https://travis-ci.org/akeneo-labs/ExtensionStarter)

## Requirements


| ExtensionStarter | Akeneo PIM Community Edition |
|:----------------:|:----------------------------:|
| v0.1.*           | v1.5.*                       |

## Installation

Add the following dependency to your Akeneo PIM project with this shell command:

```
composer require "akeneo-labs/extension-starter" "0.1.0";
```

Register your new bundle in your AppKernel.php,

```
$bundles = [
    new Acme\Bundle\AcmeExtensionBundle\AcmeExtensionBundle(),
];
```

## Best practices

We maintain an online documentation about
[best practices for extensions development](http://docs.akeneo.com/1.5/reference/best_practices/reusable_bundles.html).
