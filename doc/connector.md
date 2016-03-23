# Using this starter kit for a connector

## Context
To write a connector, you will need to integrate your extension in an existing PIM installation.
We will use the PIM Community Standard Edition as the host of our connector.

## Initialisation
Create a new host project with the Standard Edition

```
composer create-project --prefer-dist akeneo/pim-community-standard /home/myhome/pim-project "1.5.*@stable"
cd /home/myhome/pim-project
```

This will copy a copy of the standard edition without git informations.

Then, clone the starter kit

```
composer require akeneo-labs/extension-starter 0.1.0 --prefer-source
cd vendor/akeneo-labs/extension-starter/Acme/Bundle/DemoExtensionBundle
```

At this point, you will need to reset the git information to become owner of the code.

Start by resetting git :

```
rm .git -rf`
git init
```

## Customization
You will need to rename your extension according to the chosen name.
Let's say you work for the WorldCompany and the connector name is WorldConnector.

You will need to move your component inside the vendor directory :

```
cd /home/myhome/pim-project/vendor
mkdir world-company
mv akeneo-labs/extension-starter world-company/world-connector
cd world-company/world-connector
mv Acme WorldCompany
find WorldCompany/ -name '*.php' -type f -print0 | xargs -0 sed 's#Acme#WorldCompany#g'
```
