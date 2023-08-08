Is my Network watcher currently being used? 
```
resources
| where type == "microsoft.network/networksecuritygroups"
| where properties['flowLogs'][0]['id'] contains "/subscriptions/########-####-####-####-############/resourceGroups/NetworkWatcherRG/providers/Microsoft.Network/networkWatchers/NetworkWatcher_westus2"
```

What Network Watcher is each of my NSGs using? 
```
resources
| where type == "microsoft.network/networksecuritygroups"
| project NSG = name, NetworkWatchers = properties['flowLogs'][0]['id']
```
