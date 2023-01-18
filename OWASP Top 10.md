The Ten Most Critical Web Application Security Risks

[https://owasp.org/www-project-top-ten/2017](https://owasp.org/www-project-top-ten/2017)

https://www.horangi.com/blog/real-life-examples-of-web-vulnerabilities

[https://medium.com/@cxosmo/owasp-top-10-real-world-examples-part-1-a540c4ea2df5](https://medium.com/@cxosmo/owasp-top-10-real-world-examples-part-1-a540c4ea2df5)

[https://medium.com/@cxosmo/owasp-top-10-real-world-examples-part-2-3cdb3bebc976](https://medium.com/@cxosmo/owasp-top-10-real-world-examples-part-2-3cdb3bebc976)



2017

1.  Injection - Injection flaws, such as SQL, NoSQL, and OS injection, occur when untrusted data is sent to an interpreter as part of a command or query. The attacker’s hostile data can trick the interpreter into executing unintended commands or accessing data without proper authorization.

1.  OS Injection, Command Injection.
2.  Source code review, SAST, DAST, Input data sanitization, filtration, escaping, validate.; limit date exposure incase of attack;

1.  Broken Authentication - Application functions related to authentication and session management are often implemented incorrectly, allowing attackers to compromise passwords, keys, or session tokens, or to exploit other implementation flaws to assume other users’ identities temporarily or permanently.

1.  Brute-force attack, credential stuffing; permits default/weak/well-know passwords; weak forget pass process; session ID; plain text/hash. session identifier in the URL;

Weak Session Cookies

1.  2FA, MFA, !=default/weak creds, strong password policies, log brute-force attempts, strong session manager.

automatic lockout after a certain number of attempts

1.  Sensitive Data Exposure - Many web applications and APIs do not properly protect sensitive data, such as financial, healthcare, and PII. Attackers may steal or modify such weakly protected data to conduct credit card fraud, identity theft, or other crimes. Sensitive data may be compromised without extra protection, such as encryption at rest or in transit, and requires special precautions when exchanged with the browser.

1.  Data in transmit in Plain text in HTTP, FTP, SMTP; backups; weak crypto/hashing; md5 or SHA1
2.  Truncation, tokenization of sensitive data; don't store SSN etc; encrypt/hash SSN etc; strong crypto/hashing/key management; TLS; disable caching of SSN etc

1.  XML External Entity (XXE) - Older or poorly configured XML processors evaluate external entity references within XML documents. External entities can be used to disclose internal files using the file URI handler, internal file shares, internal port scanning, remote code execution, and denial of service attacks

1.  <!ENTITY xxe SYSTEM "[file:///etc/passwd](file://etc/passwd)">
2.  Patch or upgrade all XML processors; implement positive ("whitelisting") server-side input validation, filtering, or sanitization to prevent hostile data within XML documents, headers, or nodes; Disable XML external entity and DTD processing in all XML parsers; SAST.

1.  Broken Access Control - Restrictions on what authenticated users are allowed to do are often not properly enforced. Attackers can exploit these flaws to access unauthorized functionality and/or data, such as access other users' accounts, view sensitive files, modify other users’ data, change access rights, etc.

1.  LFI, IDOR, Path Traversal
2.   Role-based access, disable default director listing, no backups, log access control

1.  Security Misconfiguration - This is commonly a result of insecure default configurations, incomplete or ad hoc configurations, open cloud storage, misconfigured HTTP headers, and verbose error messages containing sensitive information. Not only must all operating systems, frameworks, libraries, and applications be securely configured, but they must be patched and upgraded in a timely fashion

1.  unpatched flaws or access default accounts, unused pages, unprotected files and directories; • Unnecessary features are enabled or installed (e.g. unnecessary ports, services, pages, accounts, or privileges).; Default creds; Directory listing;
2.  Non default creds; different creds; no unused features/framework; software update; patching

1.  Cross-site scripting (XXS) - XSS flaws occur whenever an application includes untrusted data in a new web page without proper validation or escaping, or updates an existing web page with user-supplied data using a browser API that can create HTML or JavaScript. XSS allows attackers to execute scripts in the victim’s browser which can hijack user sessions, deface web sites, or redirect the user to malicious sites.

1.  session stealing, account takeover, MFA bypass,DOM node replacement or defacement (such as trojan login panels), attacks against the user's browser such as malicious software downloads, key logging, and other client-side attacks
2.  SAST, escaping, whitelist; HTML encoding;<c:out>

1.  Insecure Deserialization -

1.  S
2.  Integrity check before deserialization, deserialize in low privilege, monitoring; restricting; isolation

1.  Using component with known vulnerabilities -  Components, such as libraries, frameworks, and other software modules, run with the same privileges as the application. If a vulnerable component is exploited, such an attack can facilitate serious data loss or server takeover. Applications and APIs using components with known vulnerabilities may undermine application defenses and enable various attacks and impacts

1.  Outdated webserver/os/dbms/software; not updating patches regularly
2.  Remove unused dependencies, features, components, files, documentations; continuously check client and server side components; obtain only from official source;

1.  Insufficient Logging and Monitoring - Insufficient logging and monitoring, coupled with missing or ineffective integration with incident response, allows attackers to further attack systems, maintain persistence, pivot to more systems, and tamper, extract, or destroy data. Most breach studies show time to detect a breach is over 200 days, typically detected by external parties rather than internal processes or monitoring.

1.  • Auditable events, such as logins, failed logins, and high-value transactions are not logged. • Warnings and errors generate no, inadequate, or unclear log messages. • Logs of applications and APIs are not monitored for suspicious activity. • Logs are only stored locally. • Appropriate alerting thresholds and response escalation processes are not in place or effective.
2.  Ensure all login, access control failures, and server-side input validation failures can be logged with sufficient user context to identify suspicious or malicious accounts, and held for sufficient time to allow delayed forensic analysis. • Ensure that logs are generated in a format that can be easily consumed by a centralized log management solutions. • Ensure high-value transactions have an audit trail with integrity controls to prevent tampering or deletion, such as append-only database tables or similar

2021

 1. Broken Access Control - Same as above

 2. Cryptographic Failures - Same as Sensitive Data Exposure

 3. Injection - Same as above

 4. Insecure Design

1.  design and architectural flaws, with a call for more use of threat modeling, secure design patterns, and reference architectures.

One of the factors that contribute to insecure design is the lack of business risk profiling inherent in the software or system being developed, and thus the failure to determine what level of security design is required.

insecure design not insecure implementation

1.  secure design pattern, paved road methodology, secured component library, tooling, and threat modeling;

-   Establish and use a secure development lifecycle with AppSec professionals to help evaluate and design security and privacy-related controls
-   Incorrect privilege management; incorrect password storing; forget password questions; clear text storage; unrestricted file upload

 5. Security Misconfiguration - Same as above

 6. Vulnerable and Outdated Components - Same as above

 7. Identification and Authentication Failures - Same as Broken Authentication

 8. Software and Data Integrity Failures

1.  Related to software updates, critical data, and CI/CD pipelines without verifying integrity

Software and data integrity failures relate to code and infrastructure that does not protect against integrity violations. An example of this is where an application relies upon plugins, libraries, or modules from untrusted sources, repositories, and content delivery networks (CDNs). An insecure CI/CD pipeline can introduce the potential for unauthorized access, malicious code, or system compromise. Lastly, many applications now include auto-update functionality, where updates are downloaded without sufficient integrity verification and applied to the previously trusted application. Attackers could potentially upload their own updates to be distributed and run on all installations. Another example is where objects or data are encoded or serialized into a structure that an attacker can see and modify is vulnerable to insecure deserialization.

1.  Use digital signatures or similar mechanisms;

Review process for code and configuration changes to minimize the chance that malicious code or configuration could be introduced into your software pipeline

Ensure that unsigned or unencrypted serialized data is not sent to untrusted clients without some form of integrity check or digital signature to detect tampering or replay of the serialized data

 9. Security Logging and Monitoring Failures - Same as above


10. **Server-side Request Forgery**
	[[A10 - SSRF]]
