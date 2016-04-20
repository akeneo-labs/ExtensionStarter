# Checklist
This document list all points that should be considered when writing a connector.
It doesn’t means ou must implement all the funtionnalities, but you should check if you manage them
and document the features (and limits) of your extension.

## Connectors

### Technical base

#### MySQL / MongoDB compatibility
You must check if your connector is useable with a MongoDB PIM.

#### Scalability
You should not fetch all PIM entites in a single DB request, because it can be very bad for the memory and even crash the application when dealing with large data volumes.

#### Documentation
Your connector should be well documented to ease the use and the understanding.
Either use a README file or a “doc” folder to store your documentation.

You could also indicate PIM compatible versions. It can be done in a table listing the different version, or you can use some kind of visual indcation like shields.io badges :
![](https://img.shields.io/badge/Pim%20community-1.3-green.svg)
![](https://img.shields.io/badge/Pim%20enterprise-1.3-red.svg)

#### Installation
Installation can be part of the documentation, but you can also provide installation scripts or commands.

### Community edition
Check these exports with your connector enabled :
- Products
- Attributes
- Categories
- Families
- Attribute groups
- Attribute options
- Reference data
- Variant groups
- Associations

#### Mapping
- Your connector may need to map PIM entities fields to other fields or properties of the target system. This task is usually done in the processor.

#### Localization + translations
- You should keep in mind the localized values for import/export.
- You could also provide translations for yous cutom fields, flash messages, etc.

#### Notifications
- Your connector should emit proper notifications after import and/or export.
- Errors should be displayed.

### Enterprise edition

Check these exports with your connector enabled :
- Published products
- Drafts
- Assets
