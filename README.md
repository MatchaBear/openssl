# openssl
Guide on installing openssl, mainly to generate CSR, PEM

follow guide from here:
https://knowledge.digicert.com/solution/SO27347.html

1. install directory:
C:\Program Files (x86)\OpenSSL-Win32

2. cd C:\Program Files (x86)\OpenSSL-Win32
set OPENSSL_CONF=c:\Program Files (x86)\OpenSSL-Win32\bin\openssl.cfg
reboot

  
to create 512 hash algorithm:
openssl req –help <- https://itigloo.com/security/generate-an-openssl-certificate-request-with-sha-256-signature/


