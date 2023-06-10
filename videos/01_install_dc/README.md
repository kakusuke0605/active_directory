# 01 Installing the Domain Controller

1. Use `sconfig` to: 
    - Change the hostname
    - Change the IP address to static
    - Change the DNS server to our own IP address

2. Install the Active Directory Wndows Feature

```shell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
```

3. Set DNS Server (Using `sconfig` is also OK)
```
Get-DNSClientServerAddress
(check index number and ip address)

Set-DNSClientserverAddress -InterfaceIndex <index number> -ServerAddresses <ip address>
```

# Joining the Workstation to the domain
1. Set DNS Server
```
Get-DNSClientServerAddress
(check index number and ip address)

Set-DNSClientserverAddress -InterfaceIndex <index number> -ServerAddresses <ip address>
```

2. Add WorkStation to Domain
```
Add-Computer -DomainName xyz.com -Credential xyz\Administrator -Restart -Force
```