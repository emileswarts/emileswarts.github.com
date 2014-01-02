---
layout: post
title: 'Mysql cheatsheet'
description: Some handy mysql commands.

---

databases //show all databases
Add column to table
```
ALTER table mytable ADD (columnname1 varchar(255) NOT NULL, columnname2 enum(&#39;Y&#39;,&#39;N&#39;) DEFAULT &#39;N&#39; NOT NULL);
```


Create table with primary key
```
create table webuser_no_auto_approve(id INT(11) NOT NULL AUTO_INCREMENT PRIMARY KEY, domain VARCHAR(255) NOT NULL) engine=innodb default charset=utf8 collate=utf8_unicode_ci;
```



check database size
```
SELECT  CONCAT(sum(ROUND(((DATA_LENGTH + INDEX_LENGTH &#8211; DATA_FREE) / 1024 / 1024),2)),&#34; MB&#34;) AS Size FROM
INFORMATION_SCHEMA.TABLES where TABLE_SCHEMA like &#39;%your_db%&#39;;
```

export database, or table

```
mysqldump -u user -h localhost -p databasename tablename &gt; ~/database_or_table.sql
```

import database, or table
```

mysql -u user -h localhost -p databasename  &lt; database.sql
```



create empty table structure from other database/table
```
create table mytable like database.othertable
```



insert data from different database/table //fields have to match
```
insert into newdb select * from otherdb.olddb
```



show character encoding for table
```
show create table whatever
```



create the user, and grant some priviledges on specific db. use &#39;.&#39; for all
```
grant select, insert update, delete on newdatabase to &#39;newuser&#39; identified by &#39;pass&#39;;
```



Show last modification date
```
SELECT UPDATE_TIME FROM information_schema.tables WHERE TABLE_SCHEMA = &#39;somedb&#39;
AND TABLE_NAME = &#39;sometable&#39;;
```

Duplicate a row
```
insert into new table select NULL, col1, col2 from newtable;
```



//null represents id pk. columns need to match
To copy a column into the same table, first create the column to reflect the one you want to copy.
Then
```
update table set newcolumn = oldcolumn
```



Rename a column
```
alter table resources change enddatenew enddate datetime;
```

Rename a table
```
alter table events rename to events_backup;
```

Fulltext search
```
alter table resources add FULLTEXT(description, short_description, title);
```

Insert into table only if it is not there yet

```
insert ignore into table(title) values(&quot;test&quot;);
```

```
update albums as a, artists as b SET a.rating=b.rating where a.artist_id=b.id;
```

Update a column of a table based on another one

```
insert ignore into table(title) values(&quot;test&quot;);
```



User Privileges

Check all users privileges
```
SELECT User from mysql.user;
```


Show privileges for user
```
SHOW GRANTS FOR 'user'@'localhost';
```


Grant privileges
```
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON database.* TO username@localhost IDENTIFIED BY 'password';
```


Load CSV file
```
LOAD DATA LOCAL INFILE '/home/emile/Documents/bio.csv' INTO TABLE events FIELDS TERMINATED BY ',' LINES TERMINATED BY '\n' (event_record_id, event_code, date, title, location, event_status, type);
```


Convert table to utf-8.  Be careful
```
ALTER TABLE tbl_name CONVERT TO CHARACTER SET utf8 COLLATE utf8_general_ci;
```

