# Demo: Import Windows modules into PowerShell Core

Is not possible to run PowerShell cmdlets dedicated for Windows Desktop OS in PowerShell Core. But with PowerShell 7.0 have [Windows PowerShell Compatibility](https://github.com/PowerShell/WindowsCompatibility).

The Windows PowerShell Compatibility is a module that provides compatibility utilities that allow PowerShell Core sessions to invoke commands that are only available in Windows PowerShell. These utilities help you
to discover available modules, import those modules through proxies and then use the module commands much as if they were native to PowerShell Core.

The module is availble in [PowerShell Gallery](https://www.powershellgallery.com/packages/WindowsCompatibility)

```powershell
# All users
Install-Module -Name WindowsCompatibility

# Current user
Install-Module WindowsCompatibility -Scope CurrentUser
```

## Examples

```powershell
# Viewing the local computer's Event Log from PowerShell Core
Import-WinModule Microsoft.PowerShell.Management
Get-EventLog -Newest 5 -LogName "Application"

# View the Event Log on a remote computer from PowerShell Core
$Credential = Get-Credential
Initialize-WinSession -ComputerName SQLSERVER01 -Credential $Credential
Import-WinModule Microsoft.PowerShell.Management
Get-EventLog -Newest 5 -LogName "Application"
```

## Cmdlets

The Windows Compatibility module contains the following cmdlets:

| Cmdlet | Description |
| --- | --- |
| Add-WindowsPSModulePath | Appends the existing Windows PowerShell PSModulePath to existing PSModulePath |
| Add-WinFunction | This command defines a global function that always runs in the compatibility session |
| Compare-WinModule | Compare the set of modules for this version of PowerShell against those available in the compatibility session |
| Copy-WinModule | Copy modules from the compatibility session that are directly usable in PowerShell Core |
| Get-WinModule | Get a list of the available modules from the compatibility session |
| Import-WinModule | Import a compatibility module |
| Initialize-WinSession | Initialize the connection to the compatibility session |
| Invoke-WinCommand | Invoke a ScriptBlock that runs in the compatibility runspace |


## Import a compatibility module
This command allows you to import proxy modules from a local or remote session. 
It use the Windows Remote Management (WinRM) service.
These proxy modules will allow you to invoke cmdlets that are not directly supported in this version of PowerShell.


```powershell
# Example how to import Active Directory module
Import-WinModule activedirectory
Get-Command -Module ActiveDirectory
```
