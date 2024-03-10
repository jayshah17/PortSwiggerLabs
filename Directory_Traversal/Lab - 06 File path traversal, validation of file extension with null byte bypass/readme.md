## Lab Description: File path traversal, validation of file extension with null byte bypass

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/41e87dcd-ac77-4956-8e04-c1b80ac0a8fc)


## Solution: 

If an application requires that the user-supplied filename must end with an expected file extension, such as .png, then it might be possible to use a null byte to effectively terminate the file path before the required extension.

For example:

```
  filename=../../../etc/passwd%00.png
  NOTE -%00 is a null byte that is used to terminate a string in certain programming languages and can be used in URL input to trick the application into treating > the input as a different file type
```
The captured request which loads images of the website look like this,

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/abdc8603-1598-4ff1-954d-15a89d4c42ad)

Here, like all the previous labs, it loads a .jpg image.

If we give normal payload like ../../../etc/passwd , it will give us a 400 Bad Request in return .

This is because there is a security implementation being imposed here. The server only accepts i/p's which end with a .jpg file extension.

So we craft a payload in such a way that the payload we send must satisfy the condition of the server & also retreive the /etc/passwd also.

So the final payload will be `../../../etc/passwd%00.jpg`

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e4c979ea-7dcd-4341-a869-61d849075785)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9fb96525-d5cb-4a46-a371-7280c3cbb5d8)

