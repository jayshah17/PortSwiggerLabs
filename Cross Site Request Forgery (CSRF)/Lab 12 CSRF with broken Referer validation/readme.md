## Lab Dewscription: CSRF with broken Referer validation

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/749e92b0-88d0-47cc-9923-e605848ca570)

## Solution:

Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1d4713be-99a8-4502-9a6a-378ecc5c4d29)

Send the request to Burp Repeater. Observe that if you change the domain in the Referer HTTP header, the request is rejected.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c1d51760-9ba1-4678-83c0-27a15540a68f)

Copy the original domain of your lab instance and append it to the Referer header in the form of a query string. The result should look something like this:
```
Referer: https://arbitrary-incorrect-domain.net?0a84007a037bd49681013eee007a009d.web-security-academy.net
```
Send the request and observe that it is now accepted. The website seems to accept any Referer header as long as it contains the expected domain somewhere in the string.


![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6cf59d9f-67bc-4946-8c11-679e3b7040e1)


Create a CSRF proof of concept exploit as described in the solution to the CSRF vulnerability with no defenses lab and host it on the exploit server. Edit the JavaScript so that the third argument of the history.pushState() function includes a query string with your lab instance URL as follows:
```
history.pushState("", "", "/?0a84007a037bd49681013eee007a009d.web-security-academy.net")
```
This will cause the Referer header in the generated request to contain the URL of the target site in the query string, just like we tested earlier.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d88d767b-f8c4-4497-b305-f062dd700588)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9174e232-901f-453b-925f-e36978bf08dc)

View that exploit.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9535c49f-67a2-4e9a-bf81-983bcb9fe965)

This is because many browsers now strip the query string from the Referer header by default as a security measure. To override this behavior and ensure that the full URL is included in the request, go back to the exploit server and add the following header to the "Head" section:

`Referrer-Policy: unsafe-url`

Note that unlike the normal Referer header, the word "referrer" must be spelled correctly in this case.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2da09273-814c-4082-92ba-bb0f2cb585cb)
