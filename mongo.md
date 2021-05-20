## Export all database
```
mongodump -d <database_name> -o <directory_backup>
```
## Import/Restore all database
```
mongorestore -d <database_name> <directory_backup>
```

## Export single collection
```
mongoexport -d <database_name> -c <collection_name> -o <export_file_name>.json
```
## Import single collection from .json
```
mongoimport -d <database_name> -c <collection_name> <import_file_name>.json 
```
