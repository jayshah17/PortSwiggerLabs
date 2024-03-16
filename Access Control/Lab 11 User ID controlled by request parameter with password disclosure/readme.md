## Lab Description: User ID controlled by request parameter with password disclosure

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/01c92468-e540-44ca-8c4b-736162fc93d8)

## Solution:
The account page that contains the current user's existing password, prefilled in a masked input. So lets login as wiener to see what the account page has.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4401196c-78cc-481a-91ff-1258414ae603)

We can see there is a pre filled password in the password field. We can't see the password in plaintext but we can try reloading the page / view source-code to see what the password is.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/beaf6a58-5fa2-41cd-8fc0-80867e3ab25b)
So the password is prefilled with the password of the user winer which we logged in.

Now if we click on the My account link again after logging in , the apge reloads where it sends a request as below.
Change the parameter ?id=wiener to ?id=administrator.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e6aa1b7b-81f1-4278-a072-746d33c5a5d5)

Thus we have sucessfully exploited it as it leaked the admin's password in the response.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b6eb5c27-fd92-419a-aebf-99b9c7be3b06)

Password: `5uov4o4n6o9eakujmaeh`

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1554244d-fe59-4367-8c64-058550b3e940)
