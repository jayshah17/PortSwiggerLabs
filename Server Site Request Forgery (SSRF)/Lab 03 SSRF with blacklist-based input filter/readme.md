## Lab Description: SSRF with blacklist-based input filter

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/166f7aa5-a200-4a6e-bc56-af438e62b46c)

## Solution:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3fcb29db-5711-4525-8f91-4b4f5ed9fba6)

We need to find whether localhost / admin is blacklisted.

First we try giving localhost , our request is blocked.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4131c6be-d467-43c3-afb9-180817ecf0f4)

If we try in place of localhost as 127.0.0.1 then also its present in blacklist

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d1417b5a-a49c-4ac6-8204-593f9662c984)


We can use several techniques like short ip - 127.1 or 127.0.1, Long ip - 127.000.000.1 or encode the IP in several forms. 
Website to encode IP into different forms - https://ipaddress.standingtech.com/online-ip-address-converter

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/891420f3-1baf-45ea-bebb-1faef9c1cb8a)

Now we are knowing that `http://127.1/` worked but is we give `http://127.1/admin` then it blocks. So we have to find a way to manipulate `/admin`.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/11aad479-d266-4413-b2e6-96cb2d9766c5)

If we give as `http://127.1/aDmIn`, as a result we will get the result

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/677f5c9a-be03-4306-867b-0320143d863f)

We can delete the user easily with url manipulation

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/7d2749a8-7241-4049-9d32-3764566e6bd0)

Thus, we solved the lab.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/12a7f16a-343f-4817-96b9-69cdfc04152c)

