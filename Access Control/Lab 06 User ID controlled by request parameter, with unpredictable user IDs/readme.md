## Lab Description: User ID controlled by request parameter, with unpredictable user IDs

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f8cefa38-063b-4202-b7dd-147623eea6da)

## Solution:

In some applications, the exploitable parameter does not have a predictable value. For example, instead of an incrementing number, an application might use globally unique identifiers (GUIDs) to identify users. Here, an attacker might be unable to guess or predict the identifier for another user. However, the GUIDs belonging to other users might be disclosed elsewhere in the application where users are referenced, such as user messages or reviews.

Click on My Account , it takes us to login page. Use the credentials wiener:peter to login.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/95e23570-93ee-4a02-beb7-2da7fd276faa)

Once we login, we can see the API key of wiener.

Click on My Account & capture the request.

We have the GUID of wiener in the request. We need to somehow find the GUID of carlos to get his API key.

For that , click on the home page and browse through all the blog posts by carlos, Click on his username

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/60d769c7-52d4-4401-8090-076582f718ec)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6275a1ee-2a93-4e59-afbd-e8962fbac160)

Now we got the GUID of carlos - `29926d9f-198d-489e-bbe5-aed77cf08501`

Now in the My Account page , click on the link , capture the request and modify the GUID of wiener with carlos to get the API key.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/af4548ec-3d51-4567-acdb-d2fe9a88e57d)


![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/13562f83-5541-4366-8b5c-ab87382681f0)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/afb296e1-e932-4eec-bb69-8afaafbc01e2)


