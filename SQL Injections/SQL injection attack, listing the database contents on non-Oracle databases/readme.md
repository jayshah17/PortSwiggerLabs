# Lab Description:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/237ec7a5-b018-40d8-b8be-7f007bcd7d1a)

### Solution:

I find out that the number of columns is 2, with both being string columns.

### Find Users Table
The database in use here is Postgres, which holds the table information in the information_schema.tables-table.The available columns are listed. We are interested in table_name. 

So we can inject a query `  UNION SELECT table_name, table_schema from information_schema.tables-- `

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/511c89c4-d2de-48a9-88ad-47bfc1842841)

### Find Column in the table 

The information_schema.columns view holds information about the columns of each table, specifically the column_name column. The proper string to inject is ` UNION SELECT column_name, null from information_schema.columns WHERE table_name = 'users_capbdg'-- ` to form this query

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4ee61909-ddb1-4ca4-8c95-4832ea9c095a)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f7977ad5-dcaf-4496-a8b9-592554ef1b31)

### Find Username and Password Columns specifically

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d208cdce-92b6-4136-803e-c2208057bdc4)

Now we have all information to obtain the required usernames and password columns. Inject ` UNION SELECT username_aianai, password_dfxmeh from users_vqyhrj-- ` to form this query: 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/58221c55-0198-4411-bc07-a46873d950dd)

After we get the username and password, we have to login into the website with administrator credentials.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/0bd0666f-992c-4ebe-955b-25c4ba10d59d)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e21d6489-b7f6-40af-99c2-65b98f9590fc)
