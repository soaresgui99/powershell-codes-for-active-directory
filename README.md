# Useful Commands | Active Directory administration 
> This repository will help with useful commands/scripts to administrate your Active Directory.

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
- Get all the domain users
```

Get-ADUser -Filter *

```
- Get all the domain users from a specif OU
```

Get-ADUser -SearchBase "OU=Infrastructure Users,dc=mycompany.com.br" -Filter *

```
- This command will find all users with the word "Robert" in the name.
```

Get-ADUser -Filter {name -like "*Robert*"}

```
- Get all disable accounts
```

Search-ADAccount -AccountDisabled | select name

```
- Disable a single account 
```

Disable-ADAccount -Identity robert.smith

```
- Activate a single account
```

Enable-ADAccount -Identity robert.smith

```

- Get all accounts with the properties password never expires
```

Get-ADUser -Filter * -properties Name, PasswordNeverExpires | where {$_.passwordNeverExpires -eq "true" } | Select-Object DistinguishedName,Name,Enabled

```
