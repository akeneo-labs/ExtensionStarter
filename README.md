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
Your extension is meant to work as part of an existing PIM installation,
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

### Initialisation of the starter kit
Your new extension will be at src/WorldCompany/Bundle/WorldConnectorBundle 

```
cd ${PIM_PATH}/src
mkdir -p ${COMPANY_NAME}/Bundle
cd ${COMPANY_NAME}/Bundle
BUNDLE_NAME=${EXTENSION_NAME}Bundle
composer create-project akeneo-labs/extension-starter ${BUNDLE_NAME} -s alpha
```

### Customization
Custom composer.json to replace company name and extension name

```
cd ${BUNDLE_NAME}
cp doc/composer.json.dist composer.json
sed -i "s#Acme#${COMPANY_NAME}#g" composer.json
sed -i "s#acme#${COMPANY_NAME}#g" composer.json
sed -i "s#DemoExtension#${EXTENSION_NAME}#g" composer.json
sed -i "s#demo-extension#${EXTENSION_NAME}#g" composer.json
```

Rename files accordingly to the chosen names:

```
mv DemoExtensionBundle.php ${BUNDLE_NAME}.php
mv DependencyInjection/DemoExtension.php DependencyInjection/${EXTENSION_NAME}.php
```

Change namespaces accordingly:

```
find . -name '*.php' -type f -print0 | xargs -0 sed -i "s#Acme#${COMPANY_NAME}#g"
find . -name '*.php' -type f -print0 | xargs -0 sed -i "s#DemoExtension#${EXTENSION_NAME}#g"
```

And finally, clean up all the starter kit initialization files:

```
rm -f doc/*
echo "# ${EXTENSION_NAME} extension" > README.md
```

#### TODO
Working with symlink

## Best practices

We maintain an online documentation about
[best practices for extensions development]
(http://docs.akeneo.com/1.5/reference/best_practices/reusable_bundles.html).

## Other documentation
* Documentation about [creating a connector from scratch](http://docs.akeneo.com/latest/contributing/create_connector.html).
* Do not forget to check the [PIM cookbook](http://docs.akeneo.com/latest/cookbook/index.html)
