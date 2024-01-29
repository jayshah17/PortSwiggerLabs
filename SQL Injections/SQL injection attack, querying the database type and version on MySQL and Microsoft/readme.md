# Lab Description: 

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/44f9d7d6-7ecb-4d9d-bd75-90266f364739)

### Solution: 

The difference is that on MySQL (which appears to be used here), a # character is best used for beginning a comment instead of the --.

As a result of these steps, I find out that the number of columns is 2, with both being string columns.

` UNION+SELECT+'a',@@version# `

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/2e104110-d470-4e70-839b-6749320f94ed)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/c1e6486a-f95a-4f30-9027-5e7474282077)
