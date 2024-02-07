## Lab Description: File path traversal, simple case

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/45e11bcb-c33f-452d-9598-bbffbc391508)

## Solution:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/24d7e9b6-b9e6-4e6e-88fb-6b39d6063b46)

Send the request to Repeater.

Now in the filename parameter we have to test each payload by traversing back to find the /etc/passwd file.

When we give the payload as `filename=../../etc/passwd` , we cannot get the content as it has not reached to root

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1ce56bcb-da28-4459-bf12-18006061e8d5)

When we give the payload as `filename=../../../etc/passwd` , we get the contents of /etc/passwd

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4fb769e4-4385-4ee5-96d1-9fec2bd9f5d9)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f9dc2177-0590-4600-af73-8013cd405e33)
