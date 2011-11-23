---
layout: post
title: 'Mysql cheatsheet'

---


databases //show all databases
Add column to table
<pre> ALTER table mytable ADD (columnname1 varchar(255) NOT NULL, columnname2 enum(&#8216;Y&#8217;,'N&#8217;) DEFAULT &#8216;N&#8217; NOT NULL);</pre>

Create table with primary key
<pre> create table webuser_no_auto_approve(id INT(11) NOT NULL AUTO_INCREMENT PRIMARY KEY, domain VARCHAR(255) NOT NULL) engine=innodb default charset=utf8 collate=utf8_unicode_ci;</pre>
check database size
<pre>
 SELECT  CONCAT(sum(ROUND(((DATA_LENGTH + INDEX_LENGTH &#8211; DATA_FREE)
/ 1024 / 1024),2)),&#8221; MB&#8221;) AS Size FROM INFORMATION_SCHEMA.TABLES where
TABLE_SCHEMA like &#8216;%your_db%&#8217;;
</pre>
export database, or table
<pre>
mysqldump -u user -h localhost -p databasename tablename &gt; ~/database_or_table.sql
</pre>

import database, or table
<pre>
 mysql -u user -h localhost -p databasename  &lt; database.sql
 </pre>
create empty table structure from other database/table
<pre> create table mytable like database.othertable </pre>

insert data from different database/table //fields have to match
<pre> insert into newdb select * from otherdb.olddb </pre>

show character encoding for table
<pre> show create table whatever </pre>

create the user, and grant some priviledges on specific db. use &#8216;.&#8217; for all
<pre> grant select, insert update, delete on newdatabase to &#8216;newuser&#8217; identified by &#8216;pass&#8217;; </pre>

Show last modification date
<pre> SELECT UPDATE_TIME FROM information_schema.tables WHERE TABLE_SCHEMA = &#8216;somedb&#8217;
AND TABLE_NAME = &#8216;sometable&#8217;;</pre>

Duplicate a row
<pre> insert into new table select NULL, col1, col2 from newtable; </pre>

//null represents id pk. columns need to match
To copy a column into the same table, first create the column to reflect the one you want to copy.
Then 
<pre> update table set newcolumn = oldcolumn </pre>

Rename a column
<pre> alter table resources change enddatenew enddate datetime; </pre>

Rename a table
<pre>alter table events rename to events_backup;</pre>

Fulltext search
<pre> alter table resources add FULLTEXT(description, short_description, title); </pre>

Insert into table only if it is not there yet
<pre> insert ignore into table(title) values(&quot;test&quot;); </pre>

<pre> update albums as a, artists as b SET a.rating=b.rating where a.artist_id=b.id; </pre>
<pre> Update a column of a table based on another one </pre>

<pre> insert ignore into table(title) values(&quot;test&quot;); </pre>

<h2>User Privileges</h2>

<strong>Check all users privileges</strong>
<pre>SELECT User from mysql.user;</pre>

<strong>Show privileges for user </strong>
<pre>SHOW GRANTS FOR 'user'@'localhost'; </pre>

<strong>Grant privileges</strong>
<pre>GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON database.* TO username@localhost IDENTIFIED BY 'password';</pre>

<strong>Load CSV file</strong>
<pre>LOAD DATA LOCAL INFILE '/home/emile/Documents/bio.csv' INTO TABLE events FIELDS TERMINATED BY ',' LINES TERMINATED BY '\n' (event_record_id, event_code, date, title, location, event_status, type);</pre>

<strong>Convert table to utf-8.  Be careful</strong>
 <pre> ALTER TABLE tbl_name CONVERT TO CHARACTER SET utf8 COLLATE utf8_general_ci; </pre>
