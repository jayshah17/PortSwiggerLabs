## Lab Description: Unprotected admin functionality

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ae4f477e-9eeb-4d89-9231-59106135217f)

## Solution: 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c769bac7-962e-48c1-af10-01fa51ec2f17)

When the lab loads, we get the ususal shopping website.

Clicking on My Account page takes us to /login endpoint

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/33272bf6-0856-4bcc-9b3d-b0580c6cbccf)

Now we need to bypass this login page and directly access the admin page.

For that we can look for one of the common web directories like the robots.txt and sitemap.xml

robots.txt

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/9588f199-bb69-4323-a43a-3e8fdd40e85e)

We see a disallowed login entry here for the admin panel which is /administrator-panel.

On visiting the /administrator-panel directory, we get the admin panel.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b1595206-2506-4f27-8f81-d68d3525b50d)

So we click the link to delete the user carlos to solve the lab.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/adc5a016-fbdf-4f6b-8252-92df70a89141)
