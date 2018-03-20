Aggregation, Projection
=======================

```
db.inv_geraet.aggregate([
      {
         "$project": {
             "_id": 0,
            "eigenschaften": "$eigenschaften"
			}
     },
	 {
         "$unwind": "$eigenschaften"
     }
])
```

	 
	// above works 
	
	
```
	db.inv_geraet.aggregate([{
    $group: {_id: null, uniqueValues: {$addToSet: "$standort"}}
}])
```
```

db.inv_geraet.aggregate([{     $group: {_id: null, uniqueValues: {$addToSet: "$eigenschaften.key"}} }])

```

resulting document:

`{ "_id" : null, "uniqueValues" : [ "Nürnberg", "München", "Darmstadt" ] }`
	