# Salesforce DX Cheatsheet
A quick reference to common SFDX commands
<br/><br/>

## Authentication
### Connect Salesforce DX to an Org (e.g. DevHub, Sandbox, Production)
```
sfdx force:auth:web:login -d -a AhpraDevHub
```
<br/>

## Scratch Org Management
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

## Source Control
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

## Managing Org Security
<br/>

## Test and Deploy
