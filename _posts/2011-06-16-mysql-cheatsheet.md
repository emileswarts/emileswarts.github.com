---
layout: post
title: 'Mysql cheatsheet'

---


databases //show all databases
Add column to table
<pre>ALTER table mytable ADD (columnname1 varchar(255) NOT NULL, columnname2 enum(&#39;Y&#39;,&#39;N&#39;) DEFAULT &#39;N&#39; NOT NULL);</pre>

Create table with primary key
<pre>create table webuser_no_auto_approve(id INT(11) NOT NULL AUTO_INCREMENT PRIMARY KEY, domain VARCHAR(255) NOT NULL) engine=innodb default charset=utf8 collate=utf8_unicode_ci;</pre>

<br />
check database size
<pre>SELECT  CONCAT(sum(ROUND(((DATA_LENGTH + INDEX_LENGTH &#8211; DATA_FREE) / 1024 / 1024),2)),&#34; MB&#34;) AS Size FROM
INFORMATION_SCHEMA.TABLES where TABLE_SCHEMA like &#39;%your_db%&#39;;
</pre>

<br />
export database, or table
<pre>mysqldump -u user -h localhost -p databasename tablename &gt; ~/database_or_table.sql </pre>

<br />
import database, or table
<pre>mysql -u user -h localhost -p databasename  &lt; database.sql </pre>

<br />
create empty table structure from other database/table
<pre>create table mytable like database.othertable </pre>

<br />
insert data from different database/table //fields have to match
<pre>insert into newdb select * from otherdb.olddb </pre>

<br />
show character encoding for table
<pre>show create table whatever </pre>

<br />
create the user, and grant some priviledges on specific db. use &#39;.&#39; for all
<pre>grant select, insert update, delete on newdatabase to &#39;newuser&#39; identified by &#39;pass&#39;; </pre>

<br />
Show last modification date
<pre>SELECT UPDATE_TIME FROM information_schema.tables WHERE TABLE_SCHEMA = &#39;somedb&#39;
AND TABLE_NAME = &#39;sometable&#39;;</pre>

<br />
Duplicate a row
<pre>insert into new table select NULL, col1, col2 from newtable; </pre>

<br />
//null represents id pk. columns need to match
To copy a column into the same table, first create the column to reflect the one you want to copy.
Then 
<pre>update table set newcolumn = oldcolumn </pre>

<br />
Rename a column
<pre>alter table resources change enddatenew enddate datetime; </pre>

<br />
Rename a table
<pre>alter table events rename to events_backup;</pre>

<br />
Fulltext search
<pre>alter table resources add FULLTEXT(description, short_description, title); </pre>

<br />
Insert into table only if it is not there yet
<br />
<pre>insert ignore into table(title) values(&quot;test&quot;); </pre>

<br />
<pre>update albums as a, artists as b SET a.rating=b.rating where a.artist_id=b.id; </pre>
<br />

Update a column of a table based on another one 
<br />
<pre>insert ignore into table(title) values(&quot;test&quot;); </pre>

<br />
User Privileges

Check all users privileges
<pre>SELECT User from mysql.user;</pre>

Show privileges for user 
<pre>SHOW GRANTS FOR 'user'@'localhost'; </pre>

Grant privileges
<pre>GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON database.* TO username@localhost IDENTIFIED BY 'password';</pre>

Load CSV file
<pre>LOAD DATA LOCAL INFILE '/home/emile/Documents/bio.csv' INTO TABLE events FIELDS TERMINATED BY ',' LINES TERMINATED BY '\n' (event_record_id, event_code, date, title, location, event_status, type);</pre>

Convert table to utf-8.  Be careful
<pre>ALTER TABLE tbl_name CONVERT TO CHARACTER SET utf8 COLLATE utf8_general_ci; </pre>
