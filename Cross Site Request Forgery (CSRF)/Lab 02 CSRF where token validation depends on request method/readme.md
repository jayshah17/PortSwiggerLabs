## Lab Description: CSRF where token validation depends on request method

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/17af89a3-64ea-4cc8-b835-b16c947c29eb)

## Solution:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/709b454a-969d-405a-a051-163cebe0c3c1)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/dae37d88-4e62-4d35-a401-1f76fa3316cc)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/68aa73a0-2f52-4ba0-a7a6-b9046a707cc9)

Change request method to Get method from Post Method 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3a0efa50-9c97-4786-b4f9-7ad88db4b289)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/a2e8cd08-1717-4dbb-a26b-bacc911c1b8d)

after that clicking Follow Redirection we will get

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ce4ef119-3cfa-454d-833a-da91ad94cd3b)

we have an extra parameter as csrf token that we can remove and make an CSRF as an POC

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2ff48836-f2a0-437a-9546-91f648f39fa5)

This is an html script which has to be hosted on exploited server

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9f19e237-efcb-4dc2-b2c7-227f77ebf079)

Hosting on exploite server 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/775a7d69-8ca3-4b8a-9ec4-133a01bc27d2)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/0d64ca23-b4f2-4cfa-9601-74d405a138e4)

Now we have to click on Deliver exploit to victim

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/bd833ab6-8857-4d36-8806-1df3f394c77f)

