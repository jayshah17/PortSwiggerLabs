## Lab Description: Multi-step process with no access control on one step

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f5db4d08-6b4b-4b47-ae8f-34e7b0c36130)


## Solution: 
Mostly developers implement strong acces controls in the first step but fail to ensure it in the subsequent steps , so we can take advantage of that to perform privilege escalation.

Admin user -
First can familiarize yourself with the admin panel by logging in using the credentials administrator:admin.

Then we can play around with the requests by loggin in as wiener & exploiting the flaw in the multistep process.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/dd7dce4e-41c2-4bfd-9aa6-27fec454714c)

Once logged in , we can go to admin panel & modify other user's privileges.

We need to upgrade wiener as admin by flawed multistep process, so lets now poke around with carlos.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5b95f111-c73b-4346-84b7-41fe2bb339fa)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/8a414cc7-f519-43b5-b00c-28bcfeeecaba)


Cookier ID : QT5EsqNXsXNUIURX5hVyoVTm7d8d7Jkq

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9198af2b-1933-4b74-a23f-8b185c3d5677)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/cfbca218-8f96-4057-9aae-d8e85ec5c479)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e450f8c8-0eba-4bf3-b1c8-b8009b969dd5)

Thus we solved the lab ,

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/49aad243-74e7-4272-860a-b1979ee48b81)

