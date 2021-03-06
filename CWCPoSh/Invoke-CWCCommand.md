# Invoke-CWCCommand
## SYNOPSIS
Will issue a command against a given machine and return the results.
## SYNTAX
```powershell
Invoke-CWCCommand -Server <String> -GUID <Guid> -User <String> -Password <String> [-Command <String>] [-TimeOut <Int32>] [-PowerShell] [-Group <String>] [<CommonParameters>]



Invoke-CWCCommand -Server <String> -GUID <Guid> [-Command <String>] [-TimeOut <Int32>] [-PowerShell] [-Group <String>] -Credentials <PSCredential> [<CommonParameters>]
```
## DESCRIPTION
Will issue a command against a given machine and return the results.
## PARAMETERS
### -Server &lt;String&gt;
The address to your Control server. Example 'https://control.labtechconsulting.com' or 'http://control.secure.me:8040'
```
Required                    true
Position                    named
Default value
Accept pipeline input       false
Accept wildcard characters  false
```
### -GUID &lt;Guid&gt;
The GUID identifier for the machine you wish to connect to.

You can retreive session info with the 'Get-CWCSessions' commandlet
```
Required                    true
Position                    named
Default value
Accept pipeline input       false
Accept wildcard characters  false
```
### -User &lt;String&gt;
User to authenticate against the Control server.
```
Required                    true
Position                    named
Default value
Accept pipeline input       false
Accept wildcard characters  false
```
### -Password &lt;String&gt;
Password to authenticate against the Control server.
```
Required                    true
Position                    named
Default value
Accept pipeline input       false
Accept wildcard characters  false
```
### -Command &lt;String&gt;
The command you wish to issue to the machine.
```
Required                    false
Position                    named
Default value
Accept pipeline input       false
Accept wildcard characters  false
```
### -TimeOut &lt;Int32&gt;
The amount of time in milliseconds that a command can execute. The default is 10000 milliseconds.
```
Required                    false
Position                    named
Default value                10000
Accept pipeline input       false
Accept wildcard characters  false
```
### -PowerShell &lt;SwitchParameter&gt;
Issues the command in a powershell session.
```
Required                    false
Position                    named
Default value                False
Accept pipeline input       false
Accept wildcard characters  false
```
### -Group &lt;String&gt;
Name of session group to use.
```
Required                    false
Position                    named
Default value                All Machines
Accept pipeline input       false
Accept wildcard characters  false
```
### -Credentials &lt;PSCredential&gt;
[PSCredential] object used to authenticate against Control.
```
Required                    true
Position                    named
Default value
Accept pipeline input       false
Accept wildcard characters  false
```
## OUTPUTS
The output of the Command provided.

## EXAMPLES
### EXAMPLE 1
```powershell
PS C:\>Invoke-CWCCommand -Server $Server -GUID $GUID -User $User -Password $Password -Command 'hostname'

Will return the hostname of the machine.
```

### EXAMPLE 2
```powershell
PS C:\>Invoke-CWCCommand -Server $Server -GUID $GUID -User $User -Password $Password -TimeOut 120000 -Command 'iwr -UseBasicParsing "https://bit.ly/ltposh" | iex; Restart-LTService' -PowerShell

Will restart the Automate agent on the target machine.
```

## NOTES
Version:        1.0

Author:         Chris Taylor

Creation Date:  1/20/2016

Purpose/Change: Initial script development 
