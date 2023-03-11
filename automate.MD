## Script to move all users from "Support" OU every Friday 

```

$day = Get-Date -Format "dddd"
if ( $day -eq "Friday"  )
{
    Get-Aduser -Filter {name -like "*condition*"} | Move-ADObject -TargetPath "OU=Support,OU=Tecnology,DC=mycompany,DC=com"
} else { 
    powershell -WindowStyle hidden -Command "& {[System.Reflection.Assembly]::LoadWithPartialName('System.Windows.Forms'); [System.Windows.Forms.MessageBox]::Show('This script only run on Friday','WARNING')}"
}

```
