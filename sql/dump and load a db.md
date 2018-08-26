Dump an existing sqlite db:
```
sqlite3 sqlite.db
```
then in the sqlite prompt:
```
sqlite> .output dump.sql
sqlite> .dump
sqlite> .exit
```
Then in the location you want to copy the db into, delete the existing DB (if any) and then run: 
```
cat dump.sql | sqlite3 db.sqlite3
```

(N.B. don't make a new DB or apply migrations - the command above creates the exact same DB as was dumped, 
including the schema (which was built when the migrations were previously applied))
