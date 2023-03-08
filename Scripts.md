# Useful Commands to help your Active Directory administration 
### Enjoy =D



- Show all Active Directory Commands: 
```

Get-Command -Module ActiveDirectory

```
- Show basic informations about domain:

```

Get-ADDomain

```
- Get all domain controllers by hostname and SO
```

Get-ADDomainController -filter * | select hostname, operatingsystem

```
- Get all password policies
```

GET-ADFineGrainedPassowrdPolicy -filter *

```
- List all password policies in the connected domain
```

Get-ADDefaultDomainPasswordPolicy

```
-   Get the users and list all properties
```

-Get-ADUser username -Properties *

```