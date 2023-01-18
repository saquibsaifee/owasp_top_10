https://owasp.org/Top10/A05_2021-Security_Misconfiguration/


This is commonly a result of insecure default configurations, incomplete or ad hoc configurations, open cloud storage, misconfigured HTTP headers, and verbose error messages containing sensitive information. Not only must all operating systems, frameworks, libraries, and applications be securely configured, but they must be patched and upgraded in a timely fashion

flaws: unpatched flaws or access default accounts, unused pages, unprotected files and directories; • Unnecessary features are enabled or installed (e.g. unnecessary ports, services, pages, accounts, or privileges).; Default creds; Directory listing;

fix: Non default creds; different creds; no unused features/framework; software update; patching

XML External Entity (XXE) - Older or poorly configured XML processors evaluate external entity references within XML documents. External entities can be used to disclose internal files using the file URI handler, internal file shares, internal port scanning, remote code execution, and denial of service attacks
1.  <!ENTITY xxe SYSTEM "[file:///etc/passwd](file://etc/passwd)">
2.  Patch or upgrade all XML processors; implement positive ("whitelisting") server-side input validation, filtering, or sanitization to prevent hostile data within XML documents, headers, or nodes; Disable XML external entity and DTD processing in all XML parsers; SAST.


## Description

The application might be vulnerable if the application is:

-   Missing appropriate security hardening across any part of the application stack or improperly configured permissions on cloud services.

-   Unnecessary features are enabled or installed (e.g., unnecessary ports, services, pages, accounts, or privileges).

-   Default accounts and their passwords are still enabled and unchanged.

-   Error handling reveals stack traces or other overly informative error messages to users.

-   For upgraded systems, the latest security features are disabled or not configured securely.

-   The security settings in the application servers, application frameworks (e.g., Struts, Spring, ASP.NET), libraries, databases, etc., are not set to secure values.

-   The server does not send security headers or directives, or they are not set to secure values.

-   The software is out of date or vulnerable (see [A06:2021-Vulnerable and Outdated Components](https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/)).


## How to Prevent

Secure installation processes should be implemented, including:

-   A repeatable hardening process makes it fast and easy to deploy another environment that is appropriately locked down. Development, QA, and production environments should all be configured identically, with different credentials used in each environment. This process should be automated to minimize the effort required to set up a new secure environment.

-   A minimal platform without any unnecessary features, components, documentation, and samples. Remove or do not install unused features and frameworks.

-   A task to review and update the configurations appropriate to all security notes, updates, and patches as part of the patch management process (see [A06:2021-Vulnerable and Outdated Components](https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/)). Review cloud storage permissions (e.g., S3 bucket permissions).

-   A segmented application architecture provides effective and secure separation between components or tenants, with segmentation, containerization, or cloud security groups (ACLs).

-   Sending security directives to clients, e.g., Security Headers.

-   An automated process to verify the effectiveness of the configurations and settings in all environments.


## Example Attack Scenarios

**Scenario #1:** The application server comes with sample applications not removed from the production server. These sample applications have known security flaws attackers use to compromise the server. Suppose one of these applications is the admin console, and default accounts weren't changed. In that case, the attacker logs in with default passwords and takes over.

**Scenario #2:** Directory listing is not disabled on the server. An attacker discovers they can simply list directories. The attacker finds and downloads the compiled Java classes, which they decompile and reverse engineer to view the code. The attacker then finds a severe access control flaw in the application.

**Scenario #3:** The application server's configuration allows detailed error messages, e.g., stack traces, to be returned to users. This potentially exposes sensitive information or underlying flaws such as component versions that are known to be vulnerable.

**Scenario #4:** A cloud service provider (CSP) has default sharing permissions open to the Internet by other CSP users. This allows sensitive data stored within cloud storage to be accessed.






