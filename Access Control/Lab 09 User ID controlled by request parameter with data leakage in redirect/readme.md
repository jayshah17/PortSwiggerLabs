## LAb Description: User ID controlled by request parameter with data leakage in redirect

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1138a929-031b-40d4-b5ad-022963884674)

## Solution:

In some cases, an application does detect when the user is not permitted to access the resource, and returns a redirect to the login page. However, the response containing the redirect might still include some sensitive data belonging to the targeted user, so the attack is still successful.

Clicking on My Account takes us to the login page where we can login as wiener useing the credentials wiener:peter.

We get the account page which displays wiener's API key - WuEiiefNNOcRknhQBlROXzibPbpzJLIK

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d7d22c47-62b7-440f-834d-0815be21cf77)

When we click on My account again, the browser sends a request which contains ?id=wiener

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/87b06dff-eb2d-4715-b91c-98d2bc19e1da)

Send the request to repeater tab. Change the value to ?id=carlos and observe the response.

We get a 302 Redirect response back .

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3ec8b2c6-54d6-4872-b99f-d599344fb7a5)

Your API Key is: `pFxPRdWmgNAb50rUfW23sFpKdkvCBvaC`

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/612b1a23-908c-492c-8b7e-8b27dcb7dcf5)

Submit the key and the lab is solved.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/aafc484c-3253-4c78-8059-ed2627d8bd50)
