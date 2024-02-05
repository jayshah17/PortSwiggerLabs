## Lab Description:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/8683b426-1036-420a-86b9-e3b63f357ded)

## Solution:
Use Burp Suite to intercept and modify a request that checks the stock level.
```sql
Modify the storeID parameter, giving it the value 1|whoami.
```
![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/24e72831-77a1-4130-b3c0-56b8e4d717ca)

We observe the current user of the hosting server

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/47b761cf-5dd4-48a3-a52c-5a29bb5aa896)
