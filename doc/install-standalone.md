# Integrated instalation

## Context
Let's say you work for the WorldCompany and the connector name is WorldExtension.
A widely used practice is to use the company name as the root namespace.

```
COMPANY_NAME=WorldCompany
PIM_PATH=/tmp/pim-standard-edition
EXTENSION_NAME=WorldExtension
```

### Initialisation of the Standard Edition
In this kind of organization, we will work *inside* the host project.

pim-standard-edition
└── src
    └── WorldCompany
        ├── WorldConnectorExtension.php
        ├── composer.json
        └── ...

Create a new host project with the Standard Edition

```
composer create-project --prefer-dist akeneo/pim-community-standard ${PIM_PATH} "1.5.*@stable"
```

This will download the standard edition without git informations.

### Initialisation of the starter kit
We will create the project in a WorldCompany (company name) folder and the new extension
will be at src/WorldCompany/WorldConnectorBundle 

```
cd ${PIM_PATH}/src
composer create-project akeneo-labs/extension-starter ${COMPANY_NAME} -s alpha
```

### Customization
Customise composer.json to replace company name and extension name

```
cd ${COMPANY_NAME}
cp doc/composer.json.dist composer.json
sed -i "s#Acme#${COMPANY_NAME}#g" composer.json
sed -i "s#acme#${COMPANY_NAME}#g" composer.json
sed -i "s#DemoExtension#${EXTENSION_NAME}#g" composer.json
sed -i "s#demo-extension#${EXTENSION_NAME}#g" composer.json
```

Rename files accordingly to the chosen names:

```
BUNDLE_NAME=${EXTENSION_NAME}Bundle
mv DemoExtensionBundle.php ${BUNDLE_NAME}.php
mv DependencyInjection/DemoExtension.php DependencyInjection/${EXTENSION_NAME}.php
```

Change namespaces accordingly:

```
find . -name '*.php' -type f -print0 | xargs -0 sed -i "s#Acme#${COMPANY_NAME}#g"
find . -name '*.php' -type f -print0 | xargs -0 sed -i "s#DemoExtension#${EXTENSION_NAME}#g"
```

We must also add a PSR-4 autoload entry for our extension in `composer.json`:

```
    "autoload": {
        "psr-4": {
            "WorldCompany\\Bundle\\WorldConnectorBundle\\": "src/WorldCompany"
        }
    },
```

Then clean up all the starter kit initialization files:

```
rm -f doc/*
rm -rf vendor
echo "# ${EXTENSION_NAME} extension" > README.md
```

And finally update the composer autoloader: 

```
cd ${PIM_PATH}
composer dump-autoload
```
