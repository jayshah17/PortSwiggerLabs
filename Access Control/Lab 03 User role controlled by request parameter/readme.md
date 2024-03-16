## Lab Description: User role controlled by request parameter

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/fd98f82a-d7ee-4912-bfdf-19319dc8e03d)

## Solution: 

Some applications determine the user's access rights or role at login, and then store this information in a user-controllable location, such as a hidden field, cookie, or preset query string parameter. The application makes subsequent access control decisions based on the submitted value. For example:

https://insecure-website.com/login/home.jsp?admin=true
https://insecure-website.com/login/home.jsp?role=1
This approach is fundamentally insecure because a user can simply modify the value and gain access to functionality to which they are not authorized, such as administrative functions.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2d464b9c-b4a8-4e49-bcf3-e6077f63d47e)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/78db1f1c-4dab-4e5e-817a-c893574764ef)

It says we can view only if we are admin!

We have a login credential wiener:peter .Lets try logging in and see what requests & responses being made.

Once we hit login after entering username and password, it sends a POST request like this,

Then a GET request is made to retreive the `/myaccount` page .

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9b955bce-a473-4578-bf1c-ea3430eb559b)

Here we have an interesting cookie - Admin=false.

The reponse looks like this ,

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/36ae7ade-4109-493e-9300-ed3465cf52de)

We are logged in as wiener

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6fce3ce8-e821-4462-920b-d6c9fe827aaa)

What happens if we change the cookie value to Admin=true ?

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d211bc84-ddb8-4ea7-864a-fb45d4c9f386)

We modify all the requests where the cookie is set to Admin=false to Admin=true`

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3c99cc3d-a9cb-43cf-9c79-344ac329b701)

We are having access to Admin Panel

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3e6efee3-6917-42b5-89d9-d3e214765f3e)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/70fc37c1-4067-43ed-b211-4cbac9f43acd)

