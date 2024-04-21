## Lab Description: DOM XSS in jQuery selector sink using a hashchange event

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ab71918f-4f75-49f4-9c9f-dfc8e3af1bcd)


## Solution: 

jQuery $ selector function is used to auto-scroll to a post based on the location.hash property

Goals:Deliver an exploit that calls print

The first step is to analyse the web application. An interesting script can be found at the bottom of the page:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6918507b-d003-4188-b448-fcd0ee1b77f1)

A quick check in some online documentation shows that the script is used to scroll to a post indicated by the fragment part of the URL. Using the title of a post after a #, the browser scrolls to the post.

entering `No More Burping Out Loud Guys` after `#`

It will get redirected to there.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4c869cc4-7c5d-4be3-ae45-8d42e65d8991)

According to scrip it should come.verfiying using the console.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/20d43f4f-f788-45ec-a4f7-46bee4beaea1)

It also shows an error similar to the one shown in the previous section.

Unfortunately, I can not simply attach an onerror handler on the iframe, I guess because of differing origins of the page itself (exploit server) and the iframe.

Instead, I try to inject an img tag with an invalid source and local onerror handler:
```
<iframe src="https://0ae600e2041534388151a2c5003f00a6.web-security-academy.net/#" onload="this.src+='<img src=xxx onerror=alert()>'"></iframe>
```
And shows the alert box confirming that the script triggers on the main domain:

Now it is simple: Changing the error handler to call print and deliver the exploit to the victim:
```
<iframe src="https://0ae600e2041534388151a2c5003f00a6.web-security-academy.net/#" onload="this.src+='<img src=xxx onerror=print()>'"></iframe>
```
![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/becd1c22-8a95-4b94-8e2a-350adfaad6d9)


![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/a919a689-9dc9-4219-8e2c-50f7b45a8ef5)

