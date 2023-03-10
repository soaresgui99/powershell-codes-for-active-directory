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

Get-ADUser username -Properties *

```
- Get all the domain users
```

Get-ADUser -Filter *

```
- Get all the domain users from a specif OU
```

Get-ADUser -SearchBase "OU=Infrastructure Users,dc=mycompany,dc=com" -Filter *

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
- Find all user accounts blocked
```

Search-ADAccount -LockedOut

```
- Unlock user account
```

Unlock-ADAccount -Identity robert.smith

```
- Force user to change the password in the next logon
```

Set-ADUser - Identity username -ChangePasswordAtLogon $true

```
- Move the user OU (you will need the 'distinguishedName' from the user and OU) 
```
Move-ADObject -Identity "CN=Test User (0001),OU=Infrastructure Users,DC=mycompany,DC=com" -TargetPath "OU=HR,OU=Human Resources Users,DC=mycompany,DC=com"
```
- Get all security group members
```

Get-ADGroupMember -identity "Infrastructure Admins"

```
- This will list all security groups from domain controller
```

Get-ADGroup -filter *

```
- Create a group with a name and your members

```

Add-ADGroupMember -Identity FileServer -Members robert.smith, rachel.saints

```
Find a group with a keyword. This is useful with you don't know the exactly name.
```

Get-ADGroup -filter * | Where-Object {$_.name -like "*infra*"}

```
- Import a user list to a group
```

$members = Import-CSV C:\temp\add-to-group.csv | Select-Object -ExpandProperty samaccountname Add-GroupMember -Identity FileServer -Members $members

```
- Get all computers from domain 
```

Get-ADComputer -filter *

```
- Get all computers from an OU
```

Get-ADComputer -SearchBase "OU=Infrastructure" -Filter *

```
- Get a number of all computers from domain controller
```

Get-ADComputer -Filter * | measure

```
- Search by operating system on domain controller 
```

Get-ADComputer -filter {OperatingSystem -Like '*Windows 10*'} -property * | select name, operatingsystem

```
- This will count all the computers by operating system. Is a great command to inventory your envinroment.
```

Get-ADComputer -Filter "name -like '*'" -Properties operatingSystem | group -Property operatingSystem | Select Name,Count

```
- Remove a single computer
```

Remove-ADComputer -Identity "COMPUTER01"

```
- Add all hostnames and use the text archive above to execute a command
```

Get-Content -Path C:\temp\ComputerList.txt | Remove-ADComputer

```
- Remove computers from a specific OU
```

Get-ADComputer -SearchBase "OU=DN" -Filter * | Remove-ADComputer

```
- Get all commands about GPO
```

Get-Command -Module grouppolicy

```
- Get all GPO with status
```

Get-GPO -all | Select DisplayName, gpostatus

```

- Make a backup of every GPO 
```

Backup-GPO -All -Path E:\GPOBackup

```
