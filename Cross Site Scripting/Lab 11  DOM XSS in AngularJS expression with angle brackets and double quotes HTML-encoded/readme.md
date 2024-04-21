## Lab Description:  DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d8188ab0-052c-4fd6-a49e-892998a533a1)


## Solution: 

This lab mentions AngularJS expressions. I never used it before so a quick google search leads to the respective documentaion on the angular website.

AngularJS expressions are executed in HTML sections inside of nodes containing theng-app attribute. Fortunately, the full HTML body of the page is set as valid scope:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/484a1726-3dc8-4e7b-a1da-6dddfbb17eca)


The most trivial example given at the documentation linked above is a simple addition with {{1+2}}. So using foobar{{1+2}} as search term, the search term is displayed as:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/fa15ed15-18b0-41b6-b217-5c8e5695c16d)

This confirms the execution of the expression. The next step is to find a possibility to inject script code.

payload to trigger an alert!
```
{{$on.constructor('alert(1)')()}}
```
PortSwigger This page also contains example payloads that can be used to inject Javascript into Angular.

This raises the alert box-

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9d1023e6-0a36-4d26-bd1f-daf75a864c4f)

Lab Solved

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/742577a9-fa03-47ac-b257-a808fabdc41f)

