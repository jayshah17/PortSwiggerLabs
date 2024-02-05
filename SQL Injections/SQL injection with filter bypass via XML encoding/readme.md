## Lab Description: SQL injection with filter bypass via XML encoding

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4279fb2e-55f5-499c-8936-fd612403ce58)

## Solution: 

There are 2 xml tags where we can inject our sql injection payload ie productID & StoreId.

When testing sql injection query in productID, we get a response like this

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2a81365b-dbc0-4e01-bc7c-bd6e272d91c9)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/cd7b1d81-0beb-4fd3-b87b-7d2005960ab7)

Both show the same 403 Forbidden error

Why is it getting blocked?

> A web application firewall (WAF) will block requests that contain obvious signs of a SQL injection attack. You'll need to find a way to obfuscate your malicious query to bypass this filter. We recommend using the Hackvertor extension to do this. 
So we need to bypas WAF and execute our sql payload.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c4d9c511-a832-40a1-b508-eba1d0728abf)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d95a153c-7ae2-4239-967f-2a05cf5b7275)

### Bypass WAF -

We need to Obfuscate out xml payload inorder to bypass WAF. As per lab description we'll use Hackvertor for this

Hackvertor is a tag-based conversion tool that supports various escapes and encodings including HTML5 entities, hex, octal, unicode, url encoding etc. It uses XML-like tags to specify the type of encoding/conversion used.

NOw select the payload -> Right click -> Extensions -> Hackvertor -> Encode -> Hex entities

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5c8271d5-2df0-4290-a1fa-4d30aa05b560)

Hackvertor is used so the values will be converted to Hex Values.So, Firewall could not find this sort of injection 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/12b37402-d2ce-47bb-97a1-58923df24463)

So we can now confirm that storeID parameter is indeed vulnerable & we bypassed the WAF by encoding our payload with hex entities.

ProductID parameter doesn't seem to be vulnerable since it didn't return NULL value in response

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1ef0ccf2-a090-4b0a-bb63-a3ed73d743ee)

Craft payload -
Our payload to retrieve the admin user's credentials from users table,
```sql
UNION SELECT username || '~' || password FROM users
```
After encoding it with hex entities by using hackvertor,

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/cbb24f76-479c-4dd1-a874-fbf137c069d3)

Now login as admin to solve the lab.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/3a99d5ce-300d-4289-bd8a-36158aa2148a)
