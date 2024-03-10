## Lab Description: File path traversal, validation of start of path

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/7f11949d-d3b5-48eb-90fd-4cdd51d3d5d9)


## Solution: 

If an application requires that the user-supplied filename must start with the expected base folder, such as /var/www/images, then it might be possible to include the required base folder followed by suitable traversal sequences.

For example:

filename=/var/www/images/../../../etc/passwd
In this lab, the website loads serveral images just like the previous labs, the request captured looks like this

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e5c8b965-c18a-4daf-a7a7-2c73b2d8b34e)


When we just give ../../../etc/passwd payload in the filename= parameter , we get a 400 Bad Reques in return. This is because the server expects the filename must start with an expected base folder which is /var/www/images.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/0fe360f4-134e-4c80-a220-844d9e670b0c)

So , we need to send a payload to retreive the /etc/passwd file where the payload starts with /var/www/images.

When we give `/var/www/images/../../../etc/passwd` as payload to filename parameter we can retreive the contents of the file.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ea3fb0cb-8c9f-4663-bea1-ffbcddb93f3c)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/fe1dad33-830f-4e18-ad07-325e928bc1e3)

