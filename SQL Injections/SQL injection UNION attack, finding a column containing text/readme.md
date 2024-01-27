## Lab Description: SQL injection UNION attack, finding a column containing text

![Screenshot 2024-01-27 185316](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9036d64c-e8c7-412b-8ce9-c1214b1c682b)

### Solution:

Query made -

` SELECT * FROM someTable WHERE category = '<CATEGORY>' `

By Determining which particular column have the same data type as per previous Lab Task with injecting Null Payloads and string data 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2c82e480-d5c0-49ae-9e69-d8af5a0d26c2)

` SELECT * FROM someTable WHERE category = '<CATEGORY>' UNION SELECT '3eWHU',NULL,NULL -- `

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9810b07b-da87-4d21-b0bb-0729863dfbf6)

We need to use the UNION SELECT payload using 3 NULL values. Try adding value 33eWHU in one NULL value to see if it returns that string. If it does , then it means the column contains string data else it is not containing string data.
