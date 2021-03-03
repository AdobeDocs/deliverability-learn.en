---
title: CSR and SSL certificate request process
description:  Learn how to install SSL certificates on the subdomains you delegated to Adobe.
feature: Deliverability
kt: 
thumbnail: 
doc-type: article
activity: understand
team: ACS
---

# CSR and SSL certificate request process

Once you have delegated a domain to Adobe for sending email (see [Domain name setup](../../help/additional-resources/domain-name-setup.md)), Adobe will create and use certain subdomains for specific functions.

For example, if you have delegated email.example.com to Adobe for sending emails, Adobe will create subdomains such as the following:
* *t.email.example.com* - for tracking links
* *m.email.example.com* - for mirror pages
* *res.email.example.com* - for hosted resources (e.g. images)

It is recommended to secure these domains via SSL (HTTPS), as unsecured links (HTTP) are vulnerable to interception and will flag up warnings on modern browsers.

To install SSL certificates on these subdomains, the process involves requesting a CSR file and subsequently purchasing SSL certificates for Adobe to install or renew.

>[!CAUTION]
>
>Before installing an SSL certificate, make sure you are aware of the prerequisites listed on [this page](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#installing-ssl-certificate).

## Glossary

| Term | Description |
|--- |--- |
| CA | Certificate Authority. This is an SSL certificate provider that issues digital certificates to organizations or individuals after verifying their identity.</br>e.g. DigiCert, Symantec, etc.</br>Trusted CA - This is normally considered as 3rd party CA who issues root certificate.</br>Untrusted CA - If the certificate is signed by same organisation/company who is using the certificate, its classified as untrusted CA even when they are SSL certificates. e.g. Self Signed Certificates |
| Chain Certificate | Certificate which includes a root certificate and one or more Intermediate certificates is called a Chain or Chained Certificate.|
| CSR | CSR stands for Certificate Signing Request. It's a block of encoded text that is given to a Certificate Authority when applying for an SSL Certificate.</br>It is usually generated on the server where the certificate will be installed. |
| DER | DER (Distinguished Encoding Rules) is a certificate extension type. The .DER extension is used for binary DER encoded certificates. These files may also bear the .CER or the .CRT extension. |
| Extended Validation Certificate | An EV Certificate is a new type of certificate that is designed to prevent phishing attacks. It requires extended validation of your business and of the person ordering the certificate. |
| High Assurance Certificate | High Assurance Certificates are issued by the CA after verifying ownership of the domain name and valid business registration. |
| Intermediate CA | Certificate Authority of Intermediate Certificates included in a chain(ed) certificate.
| Intermediate Certificate | A certificate authority issues certificates in the form of a tree structure. A root certificate is the top-most certificate of the tree.</br>Any certificate in between your certificate and the root certificate is called a chain or intermediate certificate. |
| Low Assurance Certificate	| A Low Assurance Certificate, also referred as domain validated certificate includes only the domain name in the certificate (and not business/organization name). |
| PEM | PEM (Privacy Enhanced Mail) is a certificate with .PEM extension which contain ASCII Base64) data.</br>Such certificates start with a " - - - - - BEGIN CERTIFICATE- - - - -" line. |
| SAN | The Subject Alternative Names are additional host names (sites, IP addresses, common names, etc.) that should be signed as part of a single SSL Certificate. |
| Self Signed Certificate | A self-signed certificate is a certificate that is signed by the person creating it rather than a trusted certificate authority.</br>Self-signed certificates can enable the same level of encryption as a certificate signed by a CA, but there are two major drawbacks: a visitor's connection could be hijacked allowing an attacker view all the data sent (thus defeating the purpose of encrypting the connection) and the certificate cannot be revoked like a trusted certificate can. |
| SSL | SSL (Secure Sockets Layer) is the standard security technology for establishing an encrypted link between a web server and a browser. |
| Wildcard Certificate | A Wildcard Certificate can secure an unlimited number of first level sub domains on a single domain name. e.g. *.adobe.com |

## CRS and SSL process main steps

1. Client identifies the domain names to secure, and the functions to secure (tracking, mirror pages, webapps…);
Note: Adobe client Solutions/Consulting can help assist/define this; please get in touch with your client Success Manager for more information.
1. Client requests a certificate signing request (CSR) file and provides their required CSR/SSL certificate information (country, state, locality (city), organization name, organizational unit name) to Adobe client Care, via a Support ticket on Extranet;
1. Adobe client Care provides forwards the request to internal infrastructure team (Adobe TechOps);
1. Adobe TechOps generate a certificate signing request (CSR) file and provide it to the Client via client Care.
1. Client uses the CSR details and generate certificate signed by a trusted certification authority, taking care of asking for using the subjectAltName SSL extension (SAN) if it is for several domain names, and get/purchase the resulting certificate (ideally) in PEM format for Apache server.
1. Client provides SSL certificate (and intermediate chain/certificate too if applicable)  to Adobe client Care, who request internal team (Adobe TechOps) to install it;
1. (Adobe TechOps) install the certificate.
1. Client tests that certificate is successfully installed (test the URLs for each secured subdomain).
