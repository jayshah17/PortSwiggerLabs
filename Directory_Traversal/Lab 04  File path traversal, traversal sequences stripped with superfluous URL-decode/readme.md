## Lab Description: File path traversal, traversal sequences stripped with superfluous URL-decode

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2929670e-a2d6-434e-8c49-dd81de93680f)

## Solution: 

The request which loads images loooks like ,


In this lab , the server strips all the directory traversal sequences ../ & also ..%2F..%2F..%2F(double encoding), so to bypass this we can use triple encoding.

So to bypass this we use triple encoded version of `../../../etc/passwd` as `..%252F..%252F..%252Fetc%252Fpasswd` as payload.

Now we got the response back containing the response of the file.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/144ba7fd-2fc8-45b4-a9cc-3b592146ca77)

So Again we need to Url encode it then only it can decode and server will accept it.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6e223ca0-45dd-48f5-a525-b104ff44f912)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/aaa687c4-199e-4d9e-b268-da7b5552e83c)


