# SSL Bundle (GoGetSSL)
### concatenate files in one .crt file in the order:
- _domain.crt
- AAA_Certificate_Service.crt (or GoGetSSL_RSA_DV_CA.crt)
- USERTrust_RSA_Certification_Authoruty.crt

# x509

## How to generate self-signed x509 (SAML, nginx, apache, etc)  certificates

openssl req -nodes -new -x509 -keyout server.key -out server.cert
