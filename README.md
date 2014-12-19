#MongoDB Migration Tool

Uses the native mongodb driver for node.js

##Usage:

###Create
```
mav migrate -c [name]
```

###Migrate
```
mav migrate -e [local|staging|prod]
```

###Seed
```
mav seed -e [local|staging|prod]
```

Options:

```
	-h help
	-e environment
	-r rollback
	-c create [description]
```


###Anatomy of a migration

```
module.exports = function( db, done ) {
  db.collection('example').find({}, function(err, doc) {
    db.collection('example').updateOne(doc, $set: { {modified: true} }, {upsert: true}, done);
  });
};
```
