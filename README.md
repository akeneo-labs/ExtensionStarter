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

### Initialisation
Create a new host project with the Standard Edition

```
composer create-project --prefer-dist akeneo/pim-community-standard /path/to/project "1.5.*@stable"
cd /path/to/project
```

This will download the standard edition without git informations.

Then, clone the starter kit

```
composer require akeneo-labs/extension-starter 0.1.0 --prefer-dist
```

### Customization
You will need to rename your extension according to the chosen name.
Let's say you work for the WorldCompany and the connector name is WorldConnector.

You will have to move your component inside the vendor directory and rename it according to what vendor name you want to use.
A widely used practice is to use your company name.

```
cd vendor
mkdir world-company
mv akeneo-labs/extension-starter world-company/world-connector
cd world-company/world-connector
mv Acme WorldCompany
```

Change namespaces accordingly:

```
find WorldCompany/ -name '*.php' -o -name 'composer.json' -type f -print0 | xargs -0 sed -i 's#Acme#WorldCompany#g'
cd WorldCompany/Bundle/DemoExtensionBundle/
cp doc/composer.json.dist composer.json
sed -i 's#Acme#WorldCompany#g' composer.json
sed -i 's#acme#world-company#g' composer.json
```
And finally, clean up all the starter kit initialization files:

```
rm -f doc/*
echo '# Demo extension' > README.md
```

## Best practices

We maintain an online documentation about
[best practices for extensions development](http://docs.akeneo.com/1.5/reference/best_practices/reusable_bundles.html).
