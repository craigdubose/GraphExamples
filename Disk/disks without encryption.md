Are all my disks encrypted with CMK?
```
Resources
| where type =~ 'microsoft.compute/disks'
// | where properties.timeCreated contains "2023"
| where properties['encryption']['diskEncryptionSetId'] notcontains "subscription"
| where resourceGroup notcontains 'databricks'
// | project properties['uniqueId']
// | where properties.diskState =~ 'Unattached'
| project name, location, resourceGroup, subscriptionId, createdTime = todatetime(properties.timeCreated)
```
