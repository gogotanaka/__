```sql
sql = <<-SQL
SELECT
    name, venue_id, COUNT(*)
FROM
    venue_types
GROUP BY
    name, venue_id
HAVING 
    COUNT(*) > 1
SQL

hashes= ActiveRecord::Base.connection.execute(sql)
```
