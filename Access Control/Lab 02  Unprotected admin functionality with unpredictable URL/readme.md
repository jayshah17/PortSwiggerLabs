## Lab Description: Unprotected admin functionality with unpredictable URL

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/7ed681ae-7869-4f4d-b288-db6b11455efa)


## Solution:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ea9a1ed7-1e5f-4c56-bddd-1949b36690da)

To Open CLient side Code we can click ctrl + u

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/54d1a62f-5fb5-412c-9f8f-13c1f725ff32)

On seeing the source code, we see a javascript code which checks if the user is admin, then it redirects us to `/admin-mbesyq` endpoint which is the admin panel.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f6b8e913-bd31-4231-a9ed-a24d81525789)

So we could directly browse to that directory to view the admin panel.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5eb201c3-e5b6-4703-80b3-1812f0ff34a6)

Click on ther DELETE link of carlos to delete the carlos user .Thus lab is solved.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c1d5e4e6-3917-476b-80fc-344824fccfd6)
