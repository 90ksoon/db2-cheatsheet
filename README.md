# db2-cheatsheet

___


### Schemas
`SYSCAT.SCHEMATA` query schema

### Tables
`SYSIBM.SYSTABLES` for list of tables

`SYSIBM.SYSDUMMY1` is dual in oracle

### Columns
`SYSIBM.SYSCOLUMN` column information

### Functions
`SYSCAT.FUNCTIONS` query functions

### Sequence
`SYSCAT.SEQUENCES` info on sequence

### Constraints
`SYSCAT.TABCONST` table constraints

`SYSCAT.CHECKS` column checks

`SYSCAT.REFERENCES` column references

### Run Stats
`RUNSTATES ON TABLE table FOR INDEXES ALL` to run stats for all indexes

### _Syntax_

##### Create Table
```sql
CREATE TABLE (
  COLUMN1 datatype,
  COLUMN2 datatype,
  PRIMARY KEY (COLUMN1)
  )
```

##### Insert Values
```sql
INSERT INTO (COLUMN1, COLUMN2) VALUES
(VALUE1, VALUE2),
(VALUE1, VALUE2)
```

##### Triggers
```sql
CREATE OR REPLACE TRIGGER trigger_name
BEFORE | AFTER |
