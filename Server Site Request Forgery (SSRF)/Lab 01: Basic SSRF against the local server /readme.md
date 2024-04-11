## Lab Description: Basic SSRF against the local server

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f7a02088-0ae7-43ef-b6d4-254565cbe264)

## Solution: 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b964f809-f6a4-4970-b11b-d33d6d5c807d)

In an SSRF attack against the server itself, the attacker induces the application to make an HTTP request back to the server that is hosting the application, 
via its loopback network interface. This will typically involve supplying a URL with a hostname like 127.0.0.1.

```
POST /product/stock HTTP/1.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 118

stockApi=http://localhost/admin
Here, the server will fetch the contents of the /admin URL and return it to the user.
```
Now of course, the attacker could just visit the /admin URL directly. But the administrative functionality is ordinarily accessible only to suitable authenticated users. 
So an attacker who simply visits the URL directly won't see anything of interest. However, when the request to the /admin URL comes from the local machine itself, 
the normal access controls are bypassed. The application grants full access to the administrative functionality, because the request appears to originate from a trusted location.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4e52d52b-4f01-4b93-af34-65d973151aa3)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e6879350-c85a-4c79-bc49-f71f777352a0)

Change the url of stockapi to `http://localhost/admin` ,

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ab9947ad-ab2d-40e6-9e96-139ea80d41c6)

As we got 200 OK response, we are having admin privilleges to delete the current user

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4f42fe8e-47b9-4bcd-928a-06aae08d776c)

```
If we click the link to delete the user carlos , we won't be able to perform the action. The application throws an error - Admin interface only available if logged in as an administrator, or if requested from loopback
```
we can view the url to delete user Carlos as we have not logged in as admin but we are sending url as loopback user from web application.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/cdfd60ec-8a5b-4efb-92cf-4b91e7e4d59d)

We have deleted user so server shows 302 Status Code 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/11cf429a-18e8-4ae1-8537-9abcc0b15cd5)

User Carlos is deleted with SSRP Vulnerability

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3f6cee9b-ec6b-4925-8878-7aa2e5d1df2e)




