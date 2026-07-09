## Language Integrity

- Make sure to use constants, function, and class names that are documented (developer.4d.com) or used elsewhere in the project.

```4d
// BAD: non-existent constant
$build:=Folder(fk temporary folder)
// GOOD: native function alternative
$build:=Folder(Temporary folder; fk platform path)
```

```4d
// BAD: invalid class name
var $ds : cs.DataStoreClass
// GOOD: correct name
var $ds : cs.DataStoreImplementation
```

- Make sure to pass the necessary options to functions that have several modes of operation.

```4d
 // BAD: non-empty folder can't be deleted  
$folder.delete()
```
// GOOD: force delete non-empty folder
$folder.delete(Delete with contents)
