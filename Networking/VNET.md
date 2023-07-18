How many VNET peers do I have in all my VNETs? 

Resources
| where type =~ 'microsoft.network/virtualNetworks'
| extend peeringCount = array_length(properties.virtualNetworkPeerings)
| project name, peeringCount, id
// | where peeringCount > 50 # Filter to only show above a certain limit if needed. 
