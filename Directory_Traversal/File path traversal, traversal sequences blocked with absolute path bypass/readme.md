## Lab Description: File path traversal, traversal sequences blocked with absolute path bypass

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/7fd6f7b9-5f96-4d96-bf74-9d1246ef395e)

## Solution:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5f4110f8-3689-477e-84fa-61fb9d27b3c6)

In this lab, the application blocks traversal sequences but treats the supplied filename as being relative to a default working directory, so we 'll use an absolute path from the filesystem root, such as filename=/etc/passwd, to directly reference a file without using any traversal sequences.

We get the /etc/passwd file from the response.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/35d87837-49b4-4945-9963-7ce113513b9c)
