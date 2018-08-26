### To create a dump of an existing sqlite db:
1. open an sqlite db connection/prompt:
```
sqlite3 sqlite.db
```
2. then, in the sqlite prompt:
```
sqlite> .output dump.sql
sqlite> .dump
sqlite> .exit
```

### To generate a new db from the dump:
In the location you want to copy the db into, delete the existing DB (if any) and then run: 
```
cat dump.sql | sqlite3 db.sqlite3
```

(N.B. don't make a new DB or apply migrations - the command above creates the exact same DB as was dumped, 
including the schema (which was built when the migrations were previously applied))
