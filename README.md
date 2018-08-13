# Salesforce DX Cheatsheet
A quick reference to common SFDX commands
<br/><br/>

## Contents
### [Authentication](#authentication)
### [Scratch Org Management](#scratchOrgManagement)
### [Meta Data Management](#metaDataManagement)
### [Org Security](#orgSecurity)
### [Test Data Management](#testDataManagement)
### [Test and Deploy](#testAndDeploy)
<br/><br/>

## <a id="authentication"></a>Authentication
### Connect Salesforce DX to an Org (e.g. DevHub, Sandbox, Production)
```
sfdx force:auth:web:login -d -a <Name of Org to be Authenticated>
```

### Generate a Password for the Org User
```
sfdx force:user:password:generate -u <Org Name>
```
<br/>


## <a id="scratchOrgManagement"></a>Scratch Org Management
### Create a Blank SFDX Project
```
sfdx force:project:create -n <Project Name>
```

### Create a Scratch Org
```
cd <Project Name>
sfdx force:org:create -f config/project-scratch-def.json -a <Scratch Org Name> -s -d 7
```

### View a list of active Orgs
```
sfdx force:org:list
```

### View a list of all Orgs
```
sfdx force:org:list --all
```

### Remove all local inactive/expired Orgs
```
sfdx force:org:list --clean
```

### Set a Scratch Org as the Default
```
sfdx force:config:set defaultusername=<Org Name>
```
<br/>

## <a id="metaDataManagement"></a>Meta Data Management
### Push source meta data to an Org 
```
sfdx force:source:push -u <Org Name>
```

### Pull source meta data from an Org 
```
sfdx force:source:pull -u <Org Name>
```

### Copy source meta data to an Org 
```
sfdx force:source:push -u <Org Name>
```

### Pull changes from one Org to another
```
sfdx force:source:pull -u <Org Name 1>
sfdx force:source:push -u <Org Name 2>
```
<br/>

## <a id="orgSecurity"></a>Org Security
### Grant permission set to default user
```
sfdx force:user:permset:assign -n <Permission Set Name> -u <Org Name>
```
<br/>

## <a id="testDataManagement"></a>Test Data Management
### Exporting data from an Org to a file
```
sfdx force:data:tree:export -q "SELECT Name, Custom__c FROM Account WHERE Name != NULL AND Custom__c != NULL" -d ./data -u 
```

### Importing data to an Org from a single file (e.g. Account)
```
sfdx force:data:tree:import -f data/Account.json -u <Org Name>
```

### Importing data to an Org from multiple files using a plan
```
sfdx force:data:tree:import -p data/<plan file>.json -u <Org Name>
```
<br/>

## <a id="testAndDeploy"></a>Test and Deploy
### Convert source meta data to Meta Data API Package
```
mkdir <Output Directory>
sfdx force:source:convert -d <Output Directory>
```

### Check and Run All Local Tests
```
sfdx force:mdapi:deploy -w 10 -l RunLocalTests -d <Output Directory> -u <Org Name> -c
```


### Run All Local Tests and Deploy
```
sfdx force:mdapi:deploy -w 10 -l RunLocalTests -d <Output Directory> -u <Org Name>
```

### Check and Run All Tests in Org
```
sfdx force:mdapi:deploy -w 10 -l RunAllTestsInOrg -d <Output Directory> -u <Org Name> -c
```


### Run All Tests in Org and Deploy
```
sfdx force:mdapi:deploy -w 10 -l RunAllTestsInOrg -d <Output Directory> -u <Org Name>
```
