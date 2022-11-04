# openssl
Guide on installing openssl, mainly to generate CSR, PEM

follow guide from here:
https://knowledge.digicert.com/solution/SO27347.html

1. install directory:
C:\Program Files (x86)\OpenSSL-Win32

2. cd C:\Program Files (x86)\OpenSSL-Win32
set OPENSSL_CONF=c:\Program Files (x86)\OpenSSL-Win32\bin\openssl.cfg
reboot

3. error running openssl command, has not yet added into the PATH
openssl : The term 'openssl' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
At line:1 char:1
+ openssl genrsa -out private-key.key 2048
+ ~~~~~~~
    + CategoryInfo          : ObjectNotFound: (openssl:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
	
Solution: $env:path = $env:path + ";C:\Program Files (x86)\OpenSSL-Win32\bin" <- https://stackoverflow.com/questions/45506735/powershell-doesnt-recognize-openssl-even-after-i-added-it-to-the-system-path#:~:text=openssl%20%3A%20The%20term%20'openssl',is%20correct%20and%20try%20again.

4. openssl genrsa -out private-key.key 2048
found the generated key in here: C:\Users\bernh\AppData\Local\VirtualStore\Program Files (x86)\OpenSSL-Win32\bin
private-key.key
open the key file with notepad++

5. PS C:\Program Files (x86)\OpenSSL-Win32\bin> openssl req -new -key private-key.key -out csr.txt
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:SG
State or Province Name (full name) [Some-State]:""
Locality Name (eg, city) []:""
Organization Name (eg, company) [Internet Widgits Pty Ltd]:""
Organizational Unit Name (eg, section) []:""
Common Name (e.g. server FQDN or YOUR name) []:nac01.healthgrp.com.sg
Email Address []:""

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:
An optional company name []:
PS C:\Program Files (x86)\OpenSSL-Win32\bin>

6. generate ssl in one line:
https://www.rapidsslonline.com/blog/openssl-commands-basics/
openssl req -new \-newkey rsa:2048 -nodes -keyout yourdomain.key \-out yourdomain.csr \-subj "/C=SG/ST=Singapore/L=Dimanaajalah/O=Apalah, Inc./OU=IT/CN=apalah.com.sg"
openssl req -new -newkey rsa:2048 -nodes -keyout yourdomain.key -out yourdomain.csr -subj "/C=SG/ST=Singapore/L=Dimanaajalah/O=Apalah, Inc./OU=IT/CN=apalah.com.sg"

to create 512 hash algorithm:
openssl req –help <- https://itigloo.com/security/generate-an-openssl-certificate-request-with-sha-256-signature/


