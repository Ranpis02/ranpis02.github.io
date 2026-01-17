---
title: "Dump databases in MySQL"
date: 2026-01-17 16:38:22 +0800
categories: [tools]
tags: [mysql, mysqldump, docker]
---

## Export a specific database

In a Docker environment, to dump a database to the current directory, run:

```shell
docker exec -i [your_container_name] mysqldump -u root -p \
  --default-character-set=utf8mb4 \
  --set-gtid-purged=OFF \
  --skip-column-statistics \
  --no-tablespaces \
  --hex-blob \
  [...database_name] > dump.sql
```

To see which databases currently exist, run:
```shell
docker exec -i [your_container_name] mysql -u root -p -e "SHOW DATABASES;"
```

## Export all databases

To dump everything at once, add `--all-databases`:
```shell
docker exec -i [your_container_name] mysqldump -u root -p \
  --all-databases \
  --default-character-set=utf8mb4 \
  --set-gtid-purged=OFF \
  --skip-column-statistics \
  --no-tablespaces \
  --hex-blob \
  > all_databases_dump.sql
```

## Automate with a shell script

1. Create the shell script
   ```shell
   $ nano batch_export.sh
   ```

2. Add the script contents
   ```bash
   #!/bin/bash

   CONTAINER_NAME="e4f6c95a93f4"
   MYSQL_USER="root"
   MYSQL_PWD="root"
   PREFIX="gulimall_%" 
   echo "Searching for databases matching '$PREFIX'..."
   TARGET_DBS=$(docker exec -i $CONTAINER_NAME mysql -u $MYSQL_USER -p$MYSQL_PWD -N -e "SHOW DATABASES LIKE '$PREFIX';") 
   # Check if the result variable is empty
   if [ -z "$TARGET_DBS" ]; then
     echo "No databases found starting with '$PREFIX'!"
     exit 1
   fi 
   # Iterate through each database and export individually
   for DB in $TARGET_DBS; do
   echo "Exporting: $DB ..." 
   docker exec -i $CONTAINER_NAME mysqldump -u $MYSQL_USER -p$MYSQL_PWD \
       --default-character-set=utf8mb4 \
       --set-gtid-purged=OFF \
       --skip-column-statistics \
       --no-tablespaces \
       --hex-blob \
       --databases "$DB" > "${DB}.sql"
         
   # Check the exit status of the last command ($? means exit code)
   if [ $? -eq 0 ]; then
     echo "Success: ${DB}.sql created."
   else
     echo "Error: Failed to export $DB."
   fi
   done 
   echo "Batch Export Complete..."
   ```

3. Make it executable and run
   ```shell
   $ chmod +x batch_export.sh
   $ sudo ./batch_export.sh
   ```

