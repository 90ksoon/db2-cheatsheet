# db2-cheatsheet

___


### Schemas
`SYSCAT.SCHEMATA` query schema

### Tables
`SYSIBM.SYSTABLES` for list of tables

`SYSIBM.SYSDUMMY1` is dual in oracle

### Columns
`SYSIBM.SYSCOLUMNS` column information

### Functions
`SYSCAT.FUNCTIONS` query functions

`CALL SYSPROC.ADMIN_REVALIDATE_DB_OBJECTS('procedure or function', 'schema', 'name');` revalidate the object

### Sequences
`SYSCAT.SEQUENCES` info on sequence

### Triggers
`SYSCAT.TRIGGERS` info on triggers

### Constraints
`SYSCAT.TABCONST` table constraints

`SYSCAT.CHECKS` column checks

`SYSCAT.REFERENCES` column references

### Run Stats
`RUNSTATES ON TABLE table FOR INDEXES ALL` to run stats for all indexes

### TABINFO
`SELECT REORG_PENDING FROM SYSIBMADM.ADMINTABINFO where TABSCHEMA='schema' and tabname='table'` check pending reorg for table after DDL statements

### Terminal Commands

`db2 list db directory` or `db2 list database directory` list database catalog info

`db2 set serveroutput on` turn on output into stdout

`db2 reorg TABLE` reorg table

`db2 list applications` list all connecting clients

`db2 backup db DATABASE_ALIAS to DIRECTORY_PATH compress ` backup to DIR with compress option

`db2 restore database DATABASE on DIRECTORY_PATH` restore database from db file from DIRECTORY_PATH

`db2 connect reset` reset the connection

`db2 deactivate database` deactivates the db

`db2 force application all` force all application

`db2ckbkp -t DATABASE_FILE` check backup integrity

`db2 -tvmf filename.sql |tee filename.sql.out`
- **t** indicate statements are terminated with delimiter
- **v** verbose
- **m** prints number of lines affected by DML
- **f** indicate file

`db2 -td@ -vmf filename.sql >> filename.sql.out`
 - **d** delimiter specifier

 `db2 -d <database> -z <schema> -t <tablename> -e -o <filename>` extract table DDL script

### _Syntax_

##### Create Table
```sql
CREATE TABLE (
  COLUMN1 datatype,
  COLUMN2 datatype,
  COLUMN3 INT GENERATED BY DEFAULT AS IDENTITY
  PRIMARY KEY (COLUMN1)
  )

CREATE TABLE newtable AS ( SELECT * FROM oldtable ) WITH NO DATA;

RENAME TABLE schema.table TO newtable;
```

##### Check DB2 Version
`SELECT * FROM TABLE (SYSPROC.env_get_inst_info())`

##### Insert Values
```sql
INSERT INTO (COLUMN1, COLUMN2) VALUES
(VALUE1, VALUE2),
(VALUE1, VALUE2)
```

##### Column
```sql
ALTER TABLE table
ADD COLUMN column_name datatype
ADD COLUMN column_name datatype
ADD COLUMN column_name datatype;

ALTER TABLE table ADD COLUMN column datatype

ALTER TABLE table ALTER COLUMN column SET DEFAULT defaultvalue;

ALTER TABLE table ALTER COLUMN column SET NOT NULL;

ALTER TABLE table RENAME COLUMN oldcol TO newcol;

ALTER TABLE table DROP PRIMARY KEY;

ALTER TABLE table ADD PRIMARY KEY (col, col2);

DROP INDEX indexname;

CREATE UNIQUE INDEX indexname ON schema.table(col, col2);


```


#### Alter
##### Column

`ALTER TABLE table ALTER COLUMN column_name SET DATA TYPE datatype` alter column
