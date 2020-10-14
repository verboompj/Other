
Export certificate from Azure Keyvault

import locay, mark key as exportable

Export pfx

use OpenSSL to split the pfx into a key and crt file

openssl pkcs12 -in [yourfile.pfx] -nocerts -out [keyfile-encrypted.key]

 extract the private key from the pfx 

extract the certificate:

openssl pkcs12 -in [yourfile.pfx] -clcerts -nokeys -out [certificate.crt]

unencrypted 

openssl rsa -in [keyfile-encrypted.key] -out [keyfile-decrypted.key]


import Synology 
