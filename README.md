# Remote-Powershell-without-Domain
If you want to excute powershell remotely from A to B without domain, you can follow the following steps.


1)on A and B：
Enable-PSRemoting –SkipNetworkProfileCheck –Force

2)on A and B：
Set-Item WSMan:\localhost\Client\TrustedHosts -Value * -Force 

3)on A
enter-pssession -computer IP_of_B -credential User_of_B

You make the following script for no password entering

$user = "Username_of_B"
$password = ConvertTo-SecureString -String "Password_of_B" -AsPlainText -Force
$credential = New-Object -TypeName "System.Management.Automation.PSCredential" -ArgumentList $user,$password
enter-pssession -computer IP_B -credential $credential
