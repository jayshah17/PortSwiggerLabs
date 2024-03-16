## Lab Description: User role can be modified in user profile

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6cb31fc9-f77f-4499-86b9-265363e3d73f)


## Solution:

So as per the lab description, we can view the admin panel only if our roleID=2.

GET request to /myaccount -
Once we click my account link, the browser sends a req as follows.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1c229026-8f43-4791-8849-3a13025d445e)
```
GET request to /login -
```
This request retreives the login page to enter the username and password.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2b068b87-b81f-4ddc-9c4f-84fa72232753)

Login page -

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/33a3bbef-8ab6-4b92-81eb-42be20ac5726)

Now we have logged in as wiener,

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5e6d4466-9823-4742-b533-229c1817256c)

Till now we didn't see any suspicious cookie values being sent from our client

Lets move on & try to update our email.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5a602437-9241-4bf3-ba04-eda101d2ad83)

Request :
Send the request to repeater

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/37518096-6beb-49a9-9fb4-db276330df0c)

Observe that we have a roleid=1 in the JSON response.

So add the value roleid=2 in the JSON request & see what is the response in browser

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/36636638-9d12-4a6e-9166-ffb18bc09cff)

we can get to see now Admin Panel

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c5dbb2e4-6fde-496a-92fd-817b7572574a)

here we can delete Carlos and solve the lab

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/95e771c6-c4a6-4a45-b0d8-ddfaeb216792)
