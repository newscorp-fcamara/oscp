# General remote ennumeration 
- Enumerate network service versions (nmap -sV)
- DO NOT forget scanning high port ranges (nmap -p 1-65535)
- DO NOT forget UDP scans (nmap -sU )
- Try syn stealh scans if no interesting results (nmap -sS)
- DO NOT forget to banner grab weird unidentified services with netcat 
- SMB ennumeration
- Ennumerate OS , version and arch
- Ennumerate SMB shares
- Try 'guest' , 'guest' credentials 
- Take note of writable and readable SMB shares
- Read from readable shares 
- Look into any Downloads folder 
- Look into any Programs folder 
- Try to ennumerate any applications running 

# Web Application ennumeration
- Identify if virtual host needs hostname to work ( add to /etc/hosts)
- Identify backend stack
- Identify CMS 
- Bruteforce common directories and files
- DO NOT forget to try a bigger list (check /usr/share/wordlists/dirbuster)
- Try to trigger an error with a faulty http request
- DO NOT forget to ennumerate HTTP methods 
- Look at the frontend source code - find links and clues of tech stack
- Run a nikto scan 
- DO NOT forget to take notes of emails/usernames found 
- Download any files and look at metadata 


# Web apps - Getting in 
- Identify vulnerabilities in the CMS 
- Try default CMS credentials 
- Try default CMS credentials + known usernames 
- Identify vulnerabilities in the backend stack 
- Map all available user inputs in the application 
- DO NOT forget appropriate url encoding and escaping for payloads 
- Test wget or certutil requests for RCE first
- DO NOT forget writable SMB shares where you can shell the web app 
- Can you steal Windows NTLM hashes with responder via file upload ? 
- DO NOT forget to check if you can replace ssh keys with a path traversal file upload 
- DO NOT forget to check if you can read private ssh keys via path traversal 
- DO NOT forget to check for file upload vulnerabilities - if mime type, file extension or content are being filtered


# Network Services - Getting in 
- Try default credentials for services 
- Try default credentials + known usernames 
- Take note of release dates for services and OS to understand if exploits will work 
- Generate shells with msfvenom 
- DO NOT forget to use port 80 or 443 for reverse shells ( bypass any firewalls )
- DO NOT forget OS architecture 
- Use /tmp in Linux or C:\Users\Public in Windows as writable paths 

# Linux - You are in 
- Ennumerate OS and kernel version 
- Ennumerate users in /etc/passwd
- Find writable directories 
- Ennumerate kernel modules
- Ennumerate crontabs 
- Ennumerate suid binaries 
- Run linpeas and unix-privesc-check 
- Use gtfo bins to look up any privsec opportunities 
- DO NOT forget to check env variables 
- DO NOT forget to check .bashrc
- DO NOT forget to check bash history 
- Linpeas has a good exploit suggester 
- Check /var/log and /var/log/syslog for clues 
- DO NOT forget to use a custom shell if you /bin/sh is not giving you root
- DO NOT forget to check git log for any repos found 

# Linux - You got root 
- Make notes of all usernames, credentials 
- Crack any uncracked hashes 
- Tcpdump and check for any interesting network traffic 
- You can pivot with ligolo or chisel 


# Windows - Getting in 
- Smb password spray the network with cred combos and crackmapexec 
- Check if any users are AS REP roastable 
- Check if any users are Kerberos roastable 
- Check if users are dsyncable 
- Pass any hashes 
- DO NOT forget to relay hashes if possible


# Windows - You are in
- Ennumerate OS version
- Ennumerate interesting files (.txt,*.pdf,*.xls,*.xlsx,*.doc,*.docx,.kdbx) 
- DO NOT forget to look around for kepass files 
- Ennumerate programs and versions installed 
- Download PowerView 
- Download PowerUp
- Download WinPeas
- Ennumerate user privileges 
- Check if user can restart the machine 
- Does it have SeImpersonatePrivilege ?
- Is the user in the Backup Operators group ?
- Ennumerate users in admin groups 
- Check if user is admin anywhere on other machines
- You can use crackmapexec for the above
- Check for smb shares available for the user 
- Find modifiable service files 
- Check powershell history
- Ennumerate scheduled tasks
- Ennumerate paths of current services
- Check for unquoted service paths
- Dump all event logs 
- DO NOT forget dll hjacking clues 

# Windows - You got Admin 
- Dump NTLM hashes 
- Dump Domain hashes 
- Dump tickets for pass the ticket 
- DO NOT forget to crack everything  
- Pass any hashes 
- Spray any credential combos to the network 
- Check if admin is admin anywhere else  
- Check for SMB shares available
- Bye bye
