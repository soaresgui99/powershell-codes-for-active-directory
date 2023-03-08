# Useful Commands to help your Active Directory administration 
> This repository will help with useful codes to management an Active Directory environment.

### Enjoy =D

![Powershell](https://github.com/soaresgui99/powershell-codes-for-active-directory/blob/c2aa3f1b7b40d46cd2720467b3c9430c66757bf4/logo-powershell.png "Powershell")

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