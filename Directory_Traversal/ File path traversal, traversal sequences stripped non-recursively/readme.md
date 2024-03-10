## Lab Description:  File path traversal, traversal sequences stripped non-recursively

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2e3d3ff4-309d-4c1f-ac1b-2f2bf6d71235)


## Solution: 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1f66f2a9-5449-40c9-87e8-9b3af8af93aa)


When we give ../etc/passwd , the web application strips the ../ so the user input is interpreted as etc/passwd.

To bypass this we need to give nested traversal sequences like ....//etc/passwd so that even if the server strips ../ so the resulting query which will be processed by the server will be ../etc/passwd.

First we give this i/p - ....//....//etc/passwd

We get this response containing 400 Bad Request.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/18ea2d2f-7ed6-4030-8c56-1f95cb280dd9)

Now when we try `....//....//....//etc/passwd` the it gives 200 OK message.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/0f4aa231-6cb0-4c22-990c-2315d1f59158)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ea584fbe-fda3-4065-8cf7-1025759157e4)
