## Lab Description: Stored XSS into anchor href attribute with double quotes HTML-encoded

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3cec9a15-50a6-466f-b2e4-ee28221f4ef2)

## Solution:

We have a functionality to post comments.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/995e1bf9-860c-4b4f-bcc1-4c329d1a862e)

We can use the following XSS payload in the comment field to perform a stored Xss attack.
```
javascript:alert(Hello Cyber Geek)
```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6abd2359-f139-4687-bc72-859c5265ea30)

Clicking the name above your comment should trigger an alert.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/00d86421-30b6-4b12-8db1-ad7bb62dc5b2)

Lab Solved 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/83cc1566-81aa-464c-a38d-bc853b1fb674)
