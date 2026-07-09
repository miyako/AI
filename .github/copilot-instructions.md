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
// GOOD: force delete non-empty folder
$folder.delete(Delete with contents)
```

## Language Ideosyncracies

- The `ZIP Create archive` command expects parent folder as destination path:

```4d
// BAD: full path passed as destination
$zip.files.push({source: $build.file("xl/workbook.xml"); destination: "xl/workbook.xml"})
// produced entry: xl/workbook.xmlworkbook.xml
// GOOD: destination is the containing FOLDER only
$zip.files.push({source: $build.file("xl/workbook.xml"); destination: "xl/"})
// produced entry: xl/workbook.xml
```

## Modern Coding Conventions

- Prefer UTF-8 without BOM `File.setText(...; "utf-8-no-bom")` over `"utf-8"`.
- Prefer strictly character-based (faster) replacement `Replace string(...; *)` over collation-based replacement which is the default.
- Prefer the compound assignment operator: `$s+="..."` over `$s:=$s+"..."`.
- Prefer literal syntax for objects and collections: {key: value} and [a; b; c], over `New object` / `New collection`.
