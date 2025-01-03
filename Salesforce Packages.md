
**Salesforce II Generation Package**

Salesforce II Generation packages can be created - **Managed and Unmanaged** using CLI, 2 Salesforce Developer Orgs and one Scratch Org. 

1. First Salesforce Org => Namespace
2. Second Salesforce Org => Dev Hub Org and Link Namespace from first Salesforde Org with this Org. 
3. One Scratch Org => Code and Configuration of the package/

For the below commands - values are picked from sfdx-project.json. 

Commands to create package
1. sfdx force: package:create --name "E-Commerce App" -description "E-Commerce App" --packageType Managed --path force-app
- This command registers the package with Saleforce and returns a unique Id. [04taj000000589pAAA]

2. sfdx force: package:version:create --name "E-Commerce App" -description "E-Commerce App" --packageType Managed --path force-app
- This command bundles the code, configuration and uploads in to Salesforce data centers, Also gives a Link for download. My installation URL is
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

**SF Commands I used**

```
1	Create Scratch Org with default dev-hub	sf org create scratch --definition-file config/project-scratch-def.json --alias CabinScratchOrg --duration-days 7
2	Create scratch org with particular dev hub	sf org create scratch --definition-file config/project-scratch-def.json --alias MyScratchOrg --target-dev-hub MyDevHubAlias --duration-days 7
3	Scratch Org I created	Scratch org: 00DOv00000EaTMnMAN, username: test-tocfk87fxsls@example.com.
4	List all Authorized 	sfdx force:org:list
5	Get all files from scratch org to local machine	sfdx force:source:pullsfdx force
	Managed Package Created	Version create.... Create version status: Success
		Successfully created the package version [08caj00000016BRAAY]. Subscriber Package Version Id: 04taj000000589pAAA
		Package Installation URL: https://login.salesforce.com/packaging/installPackage.apexp?p0=04taj000000589pAAA
		As an alternative, you can use the "sf package:install" command.
	Set as default Dev Hub	sf config set target-dev-hub=OrgAlias
	Register the package. This time, its unlocked packsge	
		{
		  "packageDirectories": [
		    {
		      "path": "source/cabin",
		      "default": true
		    },
		    {
		      "versionName": "ver 0.1",
		      "versionNumber": "0.1.0.NEXT",
		      "path": "force-app",
		      "default": false,
		      "package": "Cabin Management System",
		      "versionDescription": "Cabin Management System"
		    }
		  ],
		  "name": "cabin",
		  "namespace": "constant",
		  "sfdcLoginUrl": "https://login.salesforce.com",
		  "sourceApiVersion": "62.0",
		  "packageAliases": {
		    "Cabin Management System": "0Hoaj0000000J97CAE"
		  }
		}
	Sf command to create package	sf package create --name "Cabin Management System" --description "Cabin Management System" --package-type Unlocked --path force-app --target-dev-hub DevHub
		
		Ids
		┌────────────┬────────────────────┐
		│ Name       │ Value              │
		├────────────┼────────────────────┤
		│ Package Id │ 0Hoaj0000000J97CAE │
		└────────────┴────────────────────┘
		        
	List all packages created  in Dev Hub 	Package Installation URL: https://login.salesforce.com/packaging/installPackage.apexp?p0=04taj00000059HBAAY
```

I installed both Managed and Unlocked 2nd Generation packages. Some differences on Objects are  best descriibed in images below

![Screenshot 2025-01-03 at 1 27 21 AM](https://github.com/user-attachments/assets/72a0f9da-fe55-4808-9153-8d894b702d1e)

![Screenshot 2025-01-03 at 1 26 48 AM](https://github.com/user-attachments/assets/cabd7544-2a11-4b3a-bacf-c62a650d3147)


![Screenshot 2025-01-03 at 1 19 08 AM](https://github.com/user-attachments/assets/aaf800d2-d035-4aa0-8737-1a6a1c964a4b)








