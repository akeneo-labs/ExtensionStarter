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

## Extensions
An extension often has more features than a connector and can impact more features of the PIM. Even if an extension has import/export capabilities, you should check the connector list to verify that all exports works well with your extension enabled.

Extensions can be very versatiles and it’s not possible to be exhaustive on what to check.

#### Dashboard
- existing widgets still work

#### Attributes type
The new attribute type should provide common features :
- Useable in grid : can the attribute be used in the product grid ,
- Sortable
- Filtrable
- Useable in Product Edit Form
- Works with Product Query Builder API
- Versionnable
- Impact on completeness
- Useable in mass edit and quick export
- Useable in variant groups
- Works with EE workflow: drafts, published products
- Compatible with Rules Engine

#### Product Edit Form
- All others components of the form should work
- the changes detection should work

#### Datagrid
- All classical features must still work: filter, sort, pagination
- Mass actions : mass edit and quick export
- columns add/remove
- check impact on other grids : associations, all settings grids

### Enterprise edition
You must also check the compatibilty of the extension with the rules engine.
