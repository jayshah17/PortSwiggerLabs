## Lab Description: URL-based access control can be circumvented

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/60e40678-7020-4e6a-b0ad-dc706423049a)


## Solution:
When the lab website loads, we straighaway see the Admin panel link present.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/8dfa5df7-9494-4723-b9e6-c08722608a95)

When we click it we get Access Denied.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/53c993fb-efce-49ee-aeca-97c2059db4ed)

Some application frameworks support various non-standard HTTP headers that can be used to override the URL in the original request, such as X-Original-URL and X-Rewrite-URL. If a web site uses rigorous front-end controls to restrict access based on URL, but the application allows the URL to be overridden via a request header, then it might be possible to bypass the access controls using a request like the following:
```
POST / HTTP/1.1
X-Original-URL: /admin/deleteUser
```
To bypass this 403, we should remove the /admin which is with the GET method in the URI in the request & add the X-Original-Url : /admin to the body of the request.
Due to frontend Validation 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b8f9c81c-4133-4a5f-a97b-1f1456402736)

we got the admin panel access

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ade6e28b-c4a5-4b85-8632-d745dc94b730)

If we click on the link to delete user carlos, we again get access-denied.

So we have to add the custom header in this request too !

Actual request -

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/fe3538de-9840-4cd0-9bff-236fa57be9fe)

Modified request
- Add the X-Original-Url: /admin/delete header
- Provide the username=carlos parameter as it is in the real query string.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e328b4df-5208-4521-a2bb-2b2ee8da55eb)

so we successfully completed the lab 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5588ae46-c3f4-4518-b11d-46111dcc69ee)
