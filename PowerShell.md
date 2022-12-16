## Windows 10 Powershell
```
Set-ExecutionPolicy RemoteSigned
```
> Select: [A] Yes to All

```
Install-Module PSWindowsUpdate
```
> Select: (default is "Y"): Enter

```
Add-WUServiceManager -MicrosoftUpdate
```
> Select: [A] Yes to All

```
Install-WindowsUpdate -MicrosoftUpdate
```
> Select: [A] Yes to All

For OpenSSH connection
```
Get-WindowsUpdate -verbose -computer $RemoteServer
or
Get-WindowsUpdate -verbose -computer $RemoteServer -AcceptAll -Install -AutoReboot
```

---
https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.3 \
https://www.sharepointdiary.com/2014/03/fix-for-powershell-script-cannot-be-loaded-because-running-scripts-is-disabled-on-this-system.html \
https://pureinfotech.com/install-windows-10-update-powershell/ \
https://christitus.com/install-windows-update-powershell/



## OpenSSH for Windows
```
Get-WindowsCapability -Online | ? Name -like 'OpenSSH*'
```

State: NotPresent - Run following
```
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
```
```
Start-Service sshd
```
```
Set-Service -Name sshd -StartupType 'Automatic'
```
```
Get-NetFirewallRule -Name *ssh*
```
```
New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force
```
---
https://raymii.org/s/tutorials/SSH_on_Windows_Server_2019.html \
https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui

---
## Software
https://chocolatey.org/install \
https://github.com/gsass1/NTop
