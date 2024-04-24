# MySQL



## TIMESTAMP

The field type `TIMESTAMP` only goes up to `2038-01-19 03:14:07`.

```sql
-- Create table
CREATE TABLE y2038 ( f_timestamp TIMESTAMP );

-- Insert record
INSERT INTO y2038 (f_timestamp) VALUES ('2038-01-19 03:14:08');

-- Error Code: 1292. Incorrect datetime value: '2038-01-19 03:14:08' for column 'f_timestamp' at row 1
```

***Possible Fix:***

The `DATETIME` field data type can be used instead. However, `TIMESTAMP` does convert the stored date and time value as `UTC` and converts it into whatever timezone MySQL is setup to run in. This does not happen with the `DATETIME` data type. If your MySQL is setup to work in the `UTC` timezone, which it normally is, then you will not see any differences.

```sql
-- Modify column from TIMESTAMP to DATETIME
ALTER TABLE y2038 MODIFY COLUMN f_timestamp DATETIME;
```

## Possible Issues

The following commands may have issues.

|Command|Description|
|---|---|
|`NOW`|Gets the current date and time.|
|`CURRENT_TIMESTAMP`|Same as the `NOW` command.|
|`LOCALTIME`|Same as the `NOW` command.|
|`SYSDATE`|Gets the system date and time.|
|`UTC_TIMESTAMP`|Gets the current timestamp.|
