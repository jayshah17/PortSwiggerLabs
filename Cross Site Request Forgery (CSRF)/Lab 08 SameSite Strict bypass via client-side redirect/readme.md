## Lab Description: SameSite Strict bypass via client-side redirect

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c3f982b9-2f6e-4c3e-a588-43a5d1c7668e)

## Solution: 

The POST `/my-account/change-email` request and notice that this doesn't contain any unpredictable tokens, so may be vulnerable to CSRF if you can bypass any SameSite cookie restrictions.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/62cff628-73b3-42c5-8965-1d244e4e971d)

Look at the response to your POST /login request. Notice that the website explicitly specifies SameSite=Strict when setting session cookies. This prevents the browser from including these cookies in cross-site requests.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/aeb48254-f2ce-4faf-b5f0-3be9b723a4d3)

Identify the suitable vulnerable part 

In the browser, go to one of the blog posts and post an arbitrary comment. Observe that you're initially sent to a confirmation page at /post/comment/confirmation?postId=x but, after a few seconds, you're taken back to the blog post.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9e7230e3-42f0-4732-ac4e-b3c98d1385eb)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c93993de-721a-4f8b-a841-ff014c02d5bf)

- Study the JavaScript and notice that this uses the postId query parameter to dynamically construct the path for the client-side redirect.

In the proxy history, right-click on the GET /post/comment/confirmation?postId=9 request and select Copy URL.And Try injecting a path traversal sequence so that the dynamically constructed redirect URL will point to your account page:

```
/post/comment/confirmation?postId=9/../../my-account
```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f3867641-e177-466b-be56-eff89c5f2ca6)

Observe that the browser normalizes this URL and successfully takes you to your account page. 

Bypass the SameSite restrictions

In the browser, go to the exploit server and create a script that induces the viewer's browser to send the GET request you just tested. The following is one possible approach:
```
<script>
    document.location = "https://0a040032041a40b885a86270005e0019.web-security-academy.net/post/comment/confirmation?postId=/../../my-account";
</script>
```
Store and view the exploit yourself.



![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9cd0ff3a-6c4a-4a76-a892-8ab506e746d2)

Observe that when the client-side redirect takes place, you still end up on your logged-in account page. This confirms that the browser included your authenticated session cookie in the second request, even though the initial comment-submission request was initiated from an arbitrary external site.

Craft an exploit-

In Burp Repeater POST /my-account/change-email request Change request method. Burp automatically generates an equivalent GET request.

Observe that the endpoint allows you to change your email address using a GET request.

Go back to the exploit server and change the postId parameter in your exploit so that the redirect causes the browser to send the equivalent GET request for changing your email address:

```
<script>
    document.location = "https://0aa8007204afc06b81d3bb9000e80069.web-security-academy.net/post/comment/confirmation?postId=../my-account/change-email?email=cyber%40yahoo.com%26submit=1";
</script>
```

    >> Note that you need to include the submit parameter and URL encode the ampersand delimiter to avoid breaking out of the postId parameter in the initial setup request.

Deliver the exploit to the victim. After a few seconds, the lab is solved-

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/553e7db8-68df-4a8d-b05f-36fdb300fe1d)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3d47eef9-dde3-4760-a6b4-aaeb90b3dacf)

