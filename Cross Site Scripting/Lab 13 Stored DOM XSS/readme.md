## Lab Description: Stored DOM XSS

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1f2f9ee1-7807-4ba0-beef-ef9e5ae94029)

## Solution: 

We have a functionality to post comments.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d197609f-1f88-4f0d-b30c-9c9b9261333a)

First i used normal alert payload for stred xss.
```
<script>alert()</script>
```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/8950894e-a731-480d-a94a-798d29fefa8c)

alert did not came.

HTML code -

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/fa9d64b0-3187-4743-9452-9c525bf03c01)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/98882eb7-29fc-4e8c-92b2-bcd4c2c01cd2)

The comments are not sent by the server directly with the response, but dynamically loaded and displayed via JavaScript:

we need come out of the <p> script </p>. for that we will use <> how out of that our scrpit will have this in front.
```
<><img src=1 onerror=alert()>
```

In an attempt to prevent XSS, the website uses the JavaScript replace() function to encode angle brackets. However, when the first argument is a string, the function only replaces the first occurrence. We exploit this vulnerability by simply including an extra set of angle brackets at the beginning of the comment. These angle brackets will be encoded, but any subsequent angle brackets will be unaffected, enabling us to effectively bypass the filter and inject HTML.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c0ce2555-1b9b-4256-9ac5-71941217b7a8)

This payload will triger an alert-

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/55f9ef8b-f7db-4a94-8aba-829aeff38c55)

