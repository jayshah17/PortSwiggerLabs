## Lab Description: Method-based access control can be circumvented

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d968f7ff-f87c-4641-8b88-e77ad0069d65)

## Solution:

This lab provides the administrator credentials to analyse the workflow of granting and revoking administrative permissions to users. It basically is just a form to select a user and using an Upgrade or Downgrade button:

In the background, POST requests are sent to /admin-roles.

Nowusing the credentials administrator:admin we have logged in as administrator

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/cf5dad22-f0c0-4999-a268-b69610a5f177)

We see that there is a link to admin panel. Clicking on admin panel takes us to this page where we can upgrade or downgrade the privileges of a user.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/7480cd9e-4030-4889-aa39-2ddabee505f0)

Click on any action && capture the request and send it top repeater as it may come handy later.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e0069b26-6de3-45c0-81c7-8a03d85de8f7)

We can see that in this POST request we have a parameter called username=carlos & action=upgrade

The above reqest upgrades the privileges of carlos user.

Now Log out of admin user and try loggin in as wiener

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9c5c3b45-a0d6-4da1-b033-ea58f5bee374)

Reload the page & capture the request & send it to repeater.

Our goal is to exploit the flawed access controls to promote ourself (wiener) to become an administrator.

So we can try to perform the role changing action as wiener by pasting the cookie value of wiener in the request made by admin to change the privileges !

Cookie of admin - P1buRv5Au9KJJFTanjY7hWmllJU3qPu05 Cookie of wiener - MngxTDUha9CdtJkEWhLLqJOrCGAGIFuk

So we change the cookie value of admin with wiener & send the request, we get the response as 401 - Unauthorized

Request -

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/a2c58f72-3267-41f5-bf1b-7ce60fd808bf)

Since this lab is based on Method-Based-Access control bypass, we can try to change the request from POST to GET. We can do this by Right click on request -> Click Change request method option.

Now it changes to a GET request,

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/8d936e72-d471-489e-9023-0667a795cc09)

So we have successfully solved this lab.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/410f8a9e-00bd-412c-a506-97f15f9bab77)

