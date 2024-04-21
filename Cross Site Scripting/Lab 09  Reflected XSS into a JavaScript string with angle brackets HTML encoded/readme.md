## Lab Description:  Reflected XSS into a JavaScript string with angle brackets HTML encoded

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/74aadbe9-ba8a-42fb-8ee3-ea9c965aad8b)


## Solution: 
Submit a random string in the search box.Observe that the random string has been reflected inside a JavaScript string.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/768b8c2a-c612-4daa-90b3-12b29941b68e)

Replace your input with the following payload to break out of the JavaScript string and inject an alert:
```
'-alert(1)-'
```
It will triger an alert.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6544c625-1f7b-466f-a73c-0a986d23d368)

Lab Solved 

 ![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3cc92110-a52e-4792-ade9-c6996176c219)
