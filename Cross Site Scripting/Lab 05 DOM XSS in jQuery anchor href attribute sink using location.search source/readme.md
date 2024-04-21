## Lab Description: DOM XSS in jQuery anchor href attribute sink using location.search source

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/31b79b2d-bbe3-41c0-9296-20ef56c5f855)

## Solution:

Clicking on the Submit feedback link on the main page of the blog leads to the path /feedback?returnPath=/.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/772c6efd-4e91-4636-8c94-9187d3894990)

back link has vulnerablity the resulting HTML-

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/bf02e5ee-bd8b-4316-9ea9-17bdf8d6f2ca)

    >> If a JavaScript library such as jQuery is being used, look out for sinks that can alter DOM elements on the page. For instance, jQuery's attr() function can change the attributes of DOM elements. If data is read from a user-controlled source like the URL, then passed to the attr() function, then it may be possible to manipulate the value sent to cause XSS. You can exploit this by modifying the URL so that the location.search source contains a malicious JavaScript URL. After the page's JavaScript applies this malicious URL to the back link's href, clicking on the back link will execute it.

payload to trigger an alert!

```javascript:alert(document.cookie)```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2c3d3e83-12c8-4782-ae9f-ca9a0602c0a8)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4d135ae5-f1ab-4381-8eb9-daf37a4a3a5d)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6701a995-dd57-4c36-b96e-867f92b76447)

Then press back to triger the alert.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/63a547bb-d247-492c-87d1-62ca8d5becd7)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/bd3a1ed6-a0ed-4c4b-92aa-3202ae62e7ee)

