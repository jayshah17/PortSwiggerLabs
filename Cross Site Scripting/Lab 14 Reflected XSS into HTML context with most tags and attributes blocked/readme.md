## Lab Description: Reflected XSS into HTML context with most tags and attributes blocked


## Solution: 

Inject a standard XSS Payload.
```
<img src=1 onerror=alert()>
```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/094292d6-24d9-4f75-9a21-6da342f84a24)

Resulted in an 400 Bad Request error and the message Tag is not allowed.


![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3460625a-8035-4dff-b442-d7e66ae31352)

This implies that the filtering is done and blocking our request.

This doesn't mean that everything is being filtered out. Example if i try the angle brackets themselves<> these are evidently not being filtered out by the web application firewall (WAF).

Resulted in no error.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/534522b1-4a12-466c-9a81-7f0a1be3837d)
