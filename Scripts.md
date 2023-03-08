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
- Obtain all domain controllers by hostname and SO
```

Get-ADDomainController -filter * | select hostname, operatingsystem

```