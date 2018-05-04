# Salesforce DX Cheatsheet
A quick reference to common SFDX commands

### Connect Salesforce DX to an Org (e.g. DevHub, Sandbox, Production)
```
sfdx force:auth:web:login -d -a AhpraDevHub
```

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
sfdx force:config:set defaultusername=<Scratch Org Name>
```
