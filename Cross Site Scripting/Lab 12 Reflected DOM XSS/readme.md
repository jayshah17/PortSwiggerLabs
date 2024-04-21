## Lab Description: Reflected DOM XSS

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c7258a4b-9e3d-49b5-9bdb-60c477e2b5c3)


## Solution: 

In Burp Suite, go to the Proxy tool caputer the request when typing hey

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/7e97594a-af6b-4bea-9eb1-1f479127d0c3)

Notice that the string is reflected in a JSON response called search-results.

From the Site Map, open the searchResults.js file and notice that the JSON response is used with an eval() function call.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/80473970-6903-4330-b0ae-f1ded5194fcb)

end the request Repeter to experiment with it.

first tried broke out java string using \".The man was shown outside the string.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/37d9531c-56f7-4264-8395-2b42d740a617)

We can actually comment that out that we use comments in JavaScript // we are going to end our java script object first.

Payload-

Now we will make out payload by -alert() instead of man we are using - because + usually url encoded.
```
\"-alert(1)}//
```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5430b49c-b9e6-4bf8-bb98-20255e39c449)

As you have injected a backslash and the site isn't escaping them, when the JSON response attempts to escape the opening double-quotes character, it adds a second backslash. The resulting double-backslash causes the escaping to be effectively canceled out. This means that the double-quotes are processed unescaped, which closes the string that should contain the search term.

An arithmetic operator (in this case the subtraction operator) is then used to separate the expressions before the alert() function is called. Finally, a closing curly bracket and two forward slashes close the JSON object early and comment out what would have been the rest of the object

Now go and search the payload and it will trigger an alert!.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/97372bf2-b517-4dfa-be40-57fb26a15ab5)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/810c42eb-21d1-4e22-ace9-108af70602b6)

Lab Solved

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/056b60f0-27da-41d6-85a3-8a3f4b3f2fbb)

