## Lab Description: DOM XSS in innerHTML sink using source location.search

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6aeb2e1e-fe7a-4061-a3f8-7deca609de64)

## Solution: 
The lab application is a blog website with search functionality.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/cd597bf3-5756-47fc-b727-ad79ac06eddc)

First try entering the following simple XSS payload to trigger an alert!

`"><script>alert(1)</script>`

But no popup came.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e1cf360d-2f41-410a-a0c7-27656aceae5e)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b14c610e-b1fa-4bf9-8ed4-45f8a4a58ec9)

The innerHTML sink doesn't accept script elements on any modern browser.
if the search argument is provided, the innerHTML of a span-element is changed dynamically. Inserting JavaScript by using `<img src="hello" onerror=alert(1)>` as search parameter results in this HTML:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d26f4252-84bb-4311-bed1-4b70b3dec011)

The resulting HTML looks like this-

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ab55076e-b1e3-4871-977c-8a9d2112c8f8)

The value of the src = 1 attribute is invalid and throws an error. This triggers the onerror event handler, which then calls the alert() function. As a result, the payload is executed whenever the user's browser attempts to load the page containing your malicious post.

This raises the alert box.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9bfe786d-430c-4dfe-92e5-1861a837cfd2)

Lab Solved,

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d88e8bd0-8488-4e90-8bdb-98ed3dcfe6a1)

