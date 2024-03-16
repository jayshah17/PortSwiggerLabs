## Lab Description: Multi-step process with no access control on one step


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


QT5EsqNXsXNUIURX5hVyoVTm7d8d7Jkq
