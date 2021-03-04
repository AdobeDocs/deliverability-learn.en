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
* *res.email.example.com* - for hosted resources (for example, images)

It is recommended to secure these domains via SSL (HTTPS), as unsecured links (HTTP) are vulnerable to interception and will flag up warnings on modern browsers.

To install SSL certificates on these subdomains, the process involves requesting a CSR file and subsequently purchasing SSL certificates for Adobe to install or renew.

>[!CAUTION]
>
>Before installing an SSL certificate, make sure you are aware of the prerequisites listed on [this page](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#installing-ssl-certificate).

## Glossary

| Term | Description |
|--- |--- |
| CA | Certificate Authority. This is an SSL certificate provider that issues digital certificates to organizations or individuals after verifying their identity.</br>e.g. DigiCert, Symantec, etc.</br>Trusted CA - This is normally considered as 3rd party CA who issues root certificate.</br>Untrusted CA - If the certificate is signed by same organisation/company who is using the certificate, its classified as untrusted CA even when they are SSL certificates. e.g. Self Signed Certificates |
| Chain Certificate | Certificate which includes a root certificate and one or more Intermediate certificates is called a Chain or Chained Certificate. |
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
1. Client requests a certificate signing request (CSR) file and provides their required CSR/SSL certificate information (country, state, locality  (city), organization name, organizational unit name) to Adobe client Care, via a Support ticket on Extranet;
1. Adobe client Care provides forwards the request to internal infrastructure team (Adobe TechOps);
1. Adobe TechOps generate a certificate signing request (CSR) file and provide it to the Client via client Care.
1. Client uses the CSR details and generate certificate signed by a trusted certification authority, taking care of asking for using the subjectAltName SSL extension (SAN) if it is for several domain names, and get/purchase the resulting certificate (ideally) in PEM format for Apache server.
1. Client provides SSL certificate (and intermediate chain/certificate too if applicable)  to Adobe client Care, who request internal team (Adobe TechOps) to install it;
1. (Adobe TechOps) install the certificate.
1. Client tests that certificate is successfully installed (test the URLs for each secured subdomain).

## Detailed steps

### Request CSR file

**If you have access to Control Panel:**

Follow the instructions to generate and download a CSR file from the Control Panel:

https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#subdomains-and-certificates

**Otherwise:**

Create Support ticket via https://adminconsole.adobe.com/ to request a CSR file from Adobe for the required subdomain(s).

**Best Practices:**

* Raise one CSR/SSL request per delegated sub-domain.
* If it is a customer requirement, it is possible to combine multiple sub-domains into a single CSR request, but only within the same environment, e.g. ACC MKT, ACC mid-sourcing and ACC RT (Message Center) are 3 separate environments.
* Create/request a new CSR before any SSL certificate renewal. Do not use previous/old CSR files from 1-2 years ago.

You will need to provide the following information :

| Information to provide in CSR Support ticket | Example value | Note |
|--- |--- |--- |
| Common Name [CN] | t.subdomain.customer.com | This could be any of the relevant domains, but usually the tracking domain. | 
| Instance URL | mycompany.campaign.adobe.com | Provide AC instance URL | 
| Subject Alternative Name [SAN]: | t.subdomain.customer.com | Make sure to include tracking subdomain as a SAN |
| State (or Province Name) [ST]	| London | If applicable. Must be full name, not abbreviated. |
| Organizational Unit Name [OU]	| IT | e.g. section. |
| Country [C] | GB | 2-letter code. For United Kingdom it's GB (not UK).</br>For full list, see here: https://www.ssl.com/csrs/country_codes/ |
| Environment URL | https://client-mid-prod1.campaign.adobe.com |
| Client Name | My Company Ltd.	|
| City/Locality Name [L] | London |
| Organization Name [O] | ACME |
| Subject Alternative Name [SAN]: | m.subdomain.customer.com |
| Subject Alternative Name [SAN]: | res.subdomain.customer.com |

>[!NOTE]
>
>Replace "subdomain.customer.com" with your delegated subdomain, and the other example values with the appropriate values.

### Validate CSR file

The text in the resulting CSR file should start with **"-----BEGIN CERTIFICATE REQUEST-----"**.

Once you receive the CSR file from Adobe, please validate it and check that the correct parameters and domain names are included.

**Steps to verify CSR File:**

1. Paste the CSR File text into an online decoder: https://www.sslshopper.com/csr-decoder.html or https://www.certlogik.com/decoder/ or https://www.entrust.net/ssl-technical/csr-viewer.cfm etc.
1. Alternatively, you can use OpenSSL command locally on a linux machine: https://www.question-defense.com/2009/09/22/use-openssl-to-verify-the-contents-of-a-csr-before-submitting-for-a-ssl-certificate
1. All checks should be OK. i.e. CSR should resolve correctly and all the details mentioned in it should match the details you provided in CSR request.

Once the CSR is verified, proceed to use the CSR to purchase an SSL certificate.

### Generate SSL Certificate

Once the CSR file is provided, the client must then purchase/generate an SSL certificate for the appropriate domains using the CSR file. 

* The certificate must be in PEM format. 
* The certificate should not be longer than 2048-bit.
* The certificate must be signed by a valid CA (Certification Authority). 
* The certificate  must include all SANs (Subject Alternative Names) as mentioned in the CSR. 
* If there are one or more intermediate certificates, client should provide ROOT + All Intermediate Certificates to Adobe.
1. You can chose certificate validity period as per their wish, but it's recommended to have certificates with longer validity period e.g. 2 years. 

>[!NOTE]
>
>Often a client has their own internal tools to request certificate or portal provided by CA to request certificate. Please be sure to use the same details as provided in CSR request to avoid any delays or discrepancies in certificate generation process.

### Validate SSL Certificate

Once the SSL certificate is generated, please validate it before sending it to Adobe; e.g. decode and check that the correct parameters and domain names are included.

**Steps to verify SSL Certificate:**

1. Make sure the certificate is in .PEM format. If they are in any other format, convert it to PEM format if possible. Normally you can convert the certificates to PEM using OpenSSL.
1. Confirm that the certificate starts with "-----BEGIN CERTIFICATE-----".
1. Copy certificate text into an online decoder, e.g. https://www.sslshopper.com/certificate-decoder.html. Or use OpenSSL command locally on a linux machine: https://www.shellhacks.com/decode-ssl-certificate/
1. Make sure certificate resolves properly including the Common Name, SAN, Issuer and Validity Period.

If SSL Certificate verification is good, verify if the certificate matches the CSR.

**Steps to compare SSL Certificate with CSR:**

1. Use https://www.sslshopper.com/certificate-key-matcher.html and do "certificate+CSR matching".
1. The certificate and CSR should match.

### Request SSL Certificate Installation

**If you have access to Control Panel**

Upload the certificate to Control Panel.

See documentation: https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html?lang=en#installing-ssl-certificate

**Otherwise: **

Create another Support ticket via https://adminconsole.adobe.com/ to request Adobe to install the certificate on the Adobe Campaign servers.

You’ll need to provide:

* The certificate file, root certificate and any intermediate certificates (attached to the ticket). Preferably in Apache PEM format.
* Ticket number of the previous ticket raised for CSR
* The same data that was provided for the CSR ticket (including environment URL, State, City/Locality, Organization Name, Organization Unit ID, Names to Secure etc.)

### Test SSL Certificate installation

Once SSL Certificates are installed and confirmed by Adobe Customer Care, before closing the SSL installation ticket, it is recommended to test that the SSL certificate has been successfully installed for all URLs.

Perform below tests + configuration in AC and tests mentioned in next steps before you confirm the ticket to be closed.

Navigate to the following URLs in your browser:

Example URLs to test with (replace email.customer.com with your subdomain):

https://subdomain.customer.com/r/test (for Webapp subdomains only, does not apply for Email subdomains)

https://t.subdomain.customer.com/r/test

https://m.subdomain.customer.com/r/test

https://res.subdomain.customer.com/r/test

A successful result will give environment information, and the address bar in the URL will not complain about an invalid SSL certificate.

Successful result in Google Chrome:

![](../../help/assets/ssl-google-successful-result.png)

Unsuccessful result in Google Chrome (SSL certificate not installed properly):

![](../../help/assets/ssl-google-unsuccessful-result.png)

You can also check the validity period of the certificate (e.g. in Google Chrome by clicking on 'Secure' > Certificate).

It is the client's responsibility to check validity period and raise a ticket to request an updated certificate to be installed, at least 2 weeks before certificate expiry (hence strongly recommended for the client to put in a process to monitor certificate expiry). You do not need to request an additional CSR, unless the CSR details have changed.

>[!NOTE]
>
>Control Panel for Adobe AWS hosted environments
>
>If your Adobe Campaign environment is hosted by Adobe in an AWS environment, you can use the Control Panel feature to verify successful installation of SSL certs &/or renew the certificates before it expires.
>
>See: https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html > Subdomains and Certificates menu on the left.

### Update any specific configuration in Adobe Campaign

You can update all references in Campaign from HTTP to HTTPS, once you are confident the SSL certificates are installed properly.

For Adobe Campaign Classic, this would usually be the URLs in Deployment Wizard and External Accounts, for tracking/mirror page/public resource domains. For ACS, this will be under "Brand Settings".

Once configurations are done in Adobe Campaign, new emails will be sent with HTTPS URLs rather than HTTP (easiest way to test is to send out a test email that contains at least one mirror page and one public resource/image). A few easy tests are below: 

1. Upload an image from AC. Once the image gets uploaded the URL returned should be HTTPS.
1. Create a test email delivery with Mirror Page, Some images + texts + unsubscription link. Send out the email to an external email ID, e.g. your Gmail address. Open the mail and ensure all the links inside the email open correctly in their HTTPS form (not HTTP) without any SSL certificate warnings/errors.

Then, new emails will be sent with HTTPS URLs rather than HTTP (easiest way to test is to send out a test email that contains at least one mirror page and one public resource/image).

Useful article: https://www.thesslstore.com/blog/what-happens-when-your-ssl-certificate-expires/

>[!CAUTION]
>
>Adobe will only support up to 2048 bit certificates. 4096 bit certificates are not yet supported.