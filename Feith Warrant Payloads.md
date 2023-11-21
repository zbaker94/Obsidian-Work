#### Warrant application
```JSON
{
	"actionAlias" : "WarrantApplicationFinalizedKickoff",
	"IDs" : [{"name":"DetailsID", "value": 99999}],
	"passthrough" : { 
		"alias" : "warrantOffenseApprovedDenied",  
		"@params": {"details_OffenseID": 999999}
	}
}
```
#### Criminal Warrant
```JSON
{
	"actionAlias" : "WarrantApprovedAction",
	"IDs" : [{"name":"DetailsOffenseID", "value": 99999}],
	"passthrough" : { 
		"alias" : "warrantOffenseApprovedDenied",  
		"@params": {"details_OffenseID": 999999}
	}
}
```