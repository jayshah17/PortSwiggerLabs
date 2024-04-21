## Lab Description: Reflected XSS into attribute with angle brackets HTML-encoded

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e9c039c4-be53-4466-8493-3c8df080f10b)

## Solution: 

Payload-

    >> Autofocus: This is an attribute that can be applied to form elements like input fields or buttons. When a page loads, the browser automatically focuses on the element that has the autofocus attribute. This means that if you have an input field with autofocus, when the page loads, that input field will be automatically selected, allowing the user to start typing without having to click on it.

    >> Onfocus: This is an event handler attribute that triggers a JavaScript function when an element receives focus. For example, if you have an input field and you want something to happen when the user clicks on it or tabs into it, you can use the "onfocus" attribute to specify a JavaScript function to execute at that moment.

```
"autofocus onfocus="alert()"
```

This HTML code creates an input field that automatically receives focus when the page loads, and when it receives focus, it triggers a JavaScript alert dialog with an empty message. This payload will triger an alert popup

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/7f67a2c7-fb16-432f-a449-3daf54dd613b)

Lab Solved 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1c75c81a-a1c2-424c-8c91-066c3e37b101)
