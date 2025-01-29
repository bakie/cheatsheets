## Databases Cheatsheet

### SQL
#### create user based on a Microsoft Entra user
```sql
create user "username" from external provider;
```

#### add a user to a role
```sql
alter role "rolename" add member "username"; 
```

#### drop user
```sql
drop user "username";
```

#### drop a user from a role
```sql
alter role "rolename" drop member "username"; 
```

#### list all users with their roles
```sql
SELECT r.name AS RoleName, m.name AS MemberName
FROM sys.database_role_members rm
JOIN sys.database_principals r ON rm.role_principal_id = r.principal_id
JOIN sys.database_principals m ON rm.member_principal_id = m.principal_id
order by m.name;
```

#### list the roles of a specific user
```sql
SELECT r.name AS RoleName
FROM sys.database_role_members rm
JOIN sys.database_principals r ON rm.role_principal_id = r.principal_id
JOIN sys.database_principals m ON rm.member_principal_id = m.principal_id
where m.name = 'spn-sc-az-haw-development';
```

#### list the security principals in a SQL server database
```sql
SELECT name, type_desc, create_date, modify_date
FROM sys.database_principals
order by type_desc;

## Principal types
# A = Application role
# C = User mapped to a certificate
# E = External user from Microsoft Entra ID
# G = Windows group
# K = User mapped to an asymmetric key
# R = Database role
# S = SQL user
# U = Windows user
# X = External group from Microsoft Entra group or applications
```
