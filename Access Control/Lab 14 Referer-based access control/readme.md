## Lab Description: Referer-based access control

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/7e6c4b82-441c-4ac8-b028-37787e42de07)


## Solution: 

Login as admin -
First lets familiarize ourselves by logging in as admin.

Clicking on admin panel link after logging in, takes us to this page where we can change privileges of a user.

When we upgrade carlos user privileges, the request sent is as follows,

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f233bdcd-c370-48fd-bb08-768cb710539e)

We can see that it has a referrer header which points to /admin.

Login as wiener -
Our goal now is to upgrade ourselves

Grab the cookie value of wiener.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/bb7e8e6c-04c5-45a5-a54d-d79cea21a990)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/a945e2cb-3312-4d17-a51c-cd4bbe6127be)


Cookie of admin - VVOipIVnKkXUOiqjZTAwTi3p9KvYwDeN Cookie of wiener - h48TnMjL0nGhApfm1Bvd4o2guVYlqHYT

Send the request where the privileges were changed by admin but by replacing admin cookie with wiener's cookie (non-admin)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/13228c4c-5ba4-417a-8198-c80b870a4440)


![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b9432655-73da-44fa-9d97-bd3cf9682e80)
