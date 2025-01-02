<div style="margin-left: 20px;">
**Salesforce II Generation Package**

Salesforce II Generation packages can be created - **Managed and Unmanaged** using CLI, 2 Salesforce Developer Orgs and one Scratch Org. 

1. Salesforce Org => Namespace
2. Salesforce Org => Dev Hub Org and Link Namespace from first Salesforde Org with this Org. 
3. Scratch Org => Code and Configuration of the package/

Commands to create package
1. sfdx force: package:create --name "E-Commerce App" -description "E-Commerce App" --packageType Managed --path force-app
2. sfdx force: package:version:create --name "E-Commerce App" -description "E-Commerce App" --packageType Managed --path force-app

The first command registers the package with Saleforce and returns a unique Id. [04taj000000589pAAA]
The second command bundles the code, configuration and uploads in to Salesforce data centers, Also gives a Link for download. My installation URL is
: https://login.salesforce.com/packaging/installPackage.apexp?p0=04taj000000589pAAA

I tested it on a fresh Salesforce Org and it installed the package and it's components.   

The sfdx-project.json gets updated after each command. The final version looks like the below

```{
  "packageDirectories": [
    {
      "path": "source/commerce",
      "default": true
    },
    {
      "versionName": "ver 0.1",
      "versionNumber": "0.1.0.NEXT",
      "path": "source/commerce",
      "default": false,
      "package": "E-Commerce App",
      "versionDescription": ""
    }
  ],
  "name": "bookscommerce",
  "namespace": "constant",
  "sfdcLoginUrl": "https://login.salesforce.com",
  "sourceApiVersion": "61.0",
  "packageAliases": {
    "E-Commerce App": "0Hoaj0000000J4HCAU",
    "E-Commerce App@0.1.0-1": "04taj000000589pAAA"
  }
}
```
</div>
