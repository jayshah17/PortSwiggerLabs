## Lab Description: SSRF with whitelist-based input filter

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/dcebbe9e-5175-4794-9cf1-e32e481e7d33)


## Solution: 

### Overview

Some applications only allow input that matches, begins with, or contains, a whitelist of permitted values. In this situation, 
you can sometimes circumvent the filter by exploiting inconsistencies in URL parsing.

You can embed credentials in a URL before the hostname, using the @ character. For example:
```
   https://expected-host:fakepassword@evil-host
```

You can use the # character to indicate a URL fragment. For example:
```
https://evil-host#expected-host
```
You can leverage the DNS naming hierarchy to place required input into a fully-qualified DNS name that you control. For example:
```
https://expected-host.evil-host
```
You can URL-encode characters to confuse the URL-parsing code. 
This is particularly useful if the code that implements the filter handles URL-encoded characters differently than the code that performs the back-end HTTP request.
Note that you can also try double-encoding characters; some servers recursively URL-decode the input they receive, which can lead to further discrepancies.

----------------------------------------------------------------------------------------------------------------------------

In this lab, there is whitelisting done at the backend. So only the whilelisted inputs will be accepted as i/p. So our normal way to access the admin panel - http://localhost/admin fails.
```
HTTP/2 400 Bad Request
Content-Type: application/json; charset=utf-8
X-Frame-Options: SAMEORIGIN
Content-Length: 58

"External stock check host must be stock.weliketoshop.net"
```
This means that the application accepts the request only if it contains stock.weliketoshop.net.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/cf373f4e-3d59-494d-8626-936218ba7b1f)

Lets try giving username@stock.weliketoshop.net. Here we can also give localhost as the username portion in the url.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/710b7d6d-9419-4ec1-9482-e5ea9eb27710)

The request is accepted & we get a 400 response back.This time it doesn't show the error External stock check host must be stock.weliketoshop.net ,which means the username part is accepted by the application.

Changing it to localhost also gives a 200 OK response.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5905365d-59e7-4247-acc4-b2a3fb8a7ec1)

Next is to use the # - URL fragment to make the server not to interpret the part after the # as a part of the request.

Now when we give the i/p url as http://localhost#@stock.weliketoshop.net, we get this error - External stock check host must be stock.weliketoshop.net

This time it doesn't show missing parameter error. This means it accepts localhost as the domain and everything after the # as a URL fragment.So the localhost word gets whitelisted here.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b77b44c5-233c-4620-84ae-c95d6694f09f)

Next on , we try to double encode the # ie (http://localhost%2523@stock.weliketoshop.net/) to bypass this.

Now we're able to accesss the localhost website.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/7908d4ed-fca9-4488-90f8-38b1bb59de4e)

We will get into /admin panel

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/92f69177-c611-45be-baa1-b451fb86bdc7)

We were successfull in deleting Carlos User

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/37822f14-4b03-4bda-83ca-e1ad63fa95ff)


![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9884022f-0b6a-4017-9f53-84bb98f20c8e)
