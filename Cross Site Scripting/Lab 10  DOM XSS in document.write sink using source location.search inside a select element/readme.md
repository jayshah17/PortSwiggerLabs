## Lab Description:  DOM XSS in document.write sink using source location.search inside a select element

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/8387ce03-c87e-4c6e-a9c7-400990c51ed9)

## Solution:

    >> The lab application is again the shop website containing the stock check feature. This time, the selection box for it is created dynamically by client side JavaScript. The defining feature that requires this is that if a store ID is provided in the URL, the store is pre-selected. For example, adding &storeId=paris to the URL will put Milan in first place of the list and selects it:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c075c05a-6903-491a-a874-4679d534d80f)

This is done by this Java script

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/bf45377f-59ec-4158-a571-cd986290f0d3)

HTML looks like this-

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/28e9b39f-bced-4635-bcaf-b55b275240dd)

I can not directly add some JavaScript in the text of the option tag. But I can complete the tags and put script content outside of the scope of the option.

Payload to script to get the content outside
```
&storeId=Paris</option>we can script here 
```
The resulting HTML looks like this-

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/63587caf-96c3-4fd8-81c0-9bd37538bacc)

The location of the `we can script here` is just a right spot for adding a script.

Modifying the URL to use-

The Payload is-
```
&storeId=Himalaya</option><script>alert(1)</script>
```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/0b33bcaa-8cee-4d22-95bd-41ed51b1284a)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/242229fc-712d-4d5b-92dd-811924961cfb)

Lab Solved 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b87b9db6-c4f9-4996-94a8-c580e57d995a)


