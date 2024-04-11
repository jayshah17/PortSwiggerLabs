## Lab Description: Basic SSRF against another back-end system

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/aceea651-e931-400d-8a18-2ac20cd30d95)

## Solution: 

Another type of trust relationship that often arises with server-side request forgery is where the application server is able to interact with other back-end systems that are not directly reachable by users.
```
Most of the internal back-end systems contain sensitive functionality that can be accessed without authentication by anyone who is able to interact with the systems.
```
Here, an attacker can exploit the SSRF vulnerability to access the administrative interface of a backend system by submitting the following request:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ffeff31a-6586-4d5c-a43f-bbdba7284d6f)


![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e7297262-9e6b-46ce-bda4-16fd16ac9881)

Send the request to intruder and add bruteforce the alst part of the IP - http://192.168.0.$0$:8080/admin.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e3687692-1db6-4ce8-8149-b7cd87209098)


![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/a3b868b8-1206-45cf-84d8-37d81b97b81e)


We got a 404 ok response for 53. So the ip of backend server is 192.168.0.53

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/be1b21d3-cc4d-429a-a714-eee6628f7966)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f0e09044-fe44-42f1-b3e8-fdc76abe029c)

we can get the url from backend server `/http://192.168.0.53:8080/admin/delete?username=carlos`

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1dbcded7-d1c6-4e0a-b47a-9eafbdc6c8e5)

So, This way we solved this lab

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5bc32ebf-627f-4734-ad2b-45eaa707e720)
