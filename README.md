wak-sqlite
==========

Wakanda SQLite Module.

About
-----

The module includes [SQLite](http://www.sqlite.org) 3.8.7.2 executable for Mac, Windows x64 and Linux x64.

The executables for Mac are built with @loader_path and for Linux with $ORIGIN, so no need to install sqlite3.

Install
-------
The module can be installed in any solution.

* Create a solution level filesystems.js, if you don't already have one, and follow the example.
```
  {
  "name":"Modules",
  "parent":"SOLUTION",
  "path":"Modules",
  "writable":true
  }  
```

That' it!

Example
-------
```
var modulesFolder = FileSystemSync('Modules');
var sql = require(modulesFolder.path + 'sql');

var desktopPath = FileSystemSync('Desktop').path;

var code = '';

code += 'create table items(id INTEGER, name TEXT);\n';
code += 'insert into items values(100, "Wakanda");\n';
code += 'insert into items values(101, "4D");\n';

code += '.mode csv\n';
code += '.output "'+desktopPath + 'sample.csv' + '"\n';

code += 'select * from items;\n';

var path = desktopPath + 'sample.sql';

sql.sqlite3(path, code);
```
