## Lab Description: CSRF where token is not tied to user session

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d4faf79f-a846-4e69-9075-00f144f22ae0)

## Solution:


When we are logging in the web application and updating email as wiener user

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/27ddbed3-6ff9-47c7-9bc4-832167173b05)


When logging as carlos user 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4114afa8-b45b-4d7c-9dbf-77d710302f47)


So by swapping csrf token of two users we can easily change email address.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3f63f8a9-1101-458f-be80-21f3a8051b3f)

Hence it is not tied to any specific user session

we have to reload the page of carlos user and get csrf token 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2c64cc78-5b19-4cbd-adb4-b01f9c9e7712)

In Burp Profeesional we have to navigate from user session of wiener to Engagement Tools -> Generate POC

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/a1d7066b-21ee-4a3e-a10c-2de826ed5308)

and take csrf of carlos user and change the email 

This way we can solve the lab easily

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/819b2c63-3bd2-4552-88d0-0446fb1ed2da)
