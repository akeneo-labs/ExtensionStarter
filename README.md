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

## Using this starter kit

### Context
Our extension is meant to work as part of an existing PIM installation,
thus we will use PIM Community Standard Edition to host the connector.
This example host container will be at /tmp/pim-standard-edition on our filesystem. 

Let's say you work for the WorldCompany and the connector name is WorldExtension.
A widely used practice is to use the company name as the root namespace.

```
COMPANY_NAME=WorldCompany
PIM_PATH=/tmp/pim-standard-edition
EXTENSION_NAME=WorldExtension
```

### Initialisation of the Standard Edition
Create a new host project with the Standard Edition

```
composer create-project --prefer-dist akeneo/pim-community-standard ${PIM_PATH} "1.5.*@stable"
```

This will download the standard edition without git informations.

At this point, you have three options to develop your extension:

- work directly in the standard edition src directory
- work in the standard edition src directory via symbolic link
- work in the vendors directory 

#### Workin in the `src` directory
In this kind of organization, we will work *inside* the host project.

```
pim-standard-edition
└── src
    └── WorldCompany
        ├── WorldConnectorExtension.php
        ├── composer.json
        └── ...
```

The complete process is detailled in the [install-standalone.md](doc/install-standalone.md) documentation.

#### Workin with a symbolic link
TODO

#### Working in the `vendor` directory
If our extension need some composer dependencies, we will have no choice but to work in the `vendor` to make it
work with our Standard Edition installation.

## Best practices
We maintain an online documentation about
[best practices for extensions development]
(http://docs.akeneo.com/1.5/reference/best_practices/reusable_bundles.html).

## Other documentation
* Documentation about [creating a connector from scratch](http://docs.akeneo.com/latest/contributing/create_connector.html).
* Do not forget to check the [PIM cookbook](http://docs.akeneo.com/latest/cookbook/index.html)
