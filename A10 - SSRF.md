OWASP: https://owasp.org/Top10/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/

Lab: https://application.security/free-application-security-training/server-side-request-forgery-in-capital-one

[https://owasp.org/Top10/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/](https://owasp.org/Top10/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/)

**The ability to manipulate a web application into sending unauthorized requests to a third-party site or resource is known as *Server Side Request Forgery (SSRF)**
	 fetching a remote resource without validating the user-supplied URL

**Mitigation**:
	 From Network layer
		Segment remote resource access functionality in separate networks to reduce the impact of SSRF
		Enforce “deny by default” firewall policies or network access control rules to block all but essential intranet traffic.
		Hints:
		~ Establish an ownership and a lifecycle for firewall rules based on applications.
		~ Log all accepted and blocked network flows on firewalls (see A09:2021-Security Logging and Monitoring Failures).
	**From Application layer:**
	-   Sanitize and validate all client-supplied input data
	-   Enforce the URL schema, port, and destination with a positive allow list
	-   Do not send raw responses to clients
	-   Disable HTTP redirections
	-   Be aware of the URL consistency to avoid attacks such as DNS rebinding and “time of check, time of use” (TOCTOU) race conditions

Do not mitigate SSRF via the use of a deny list or regular expression. Attackers have payload lists, tools, and skills to bypass deny lists.


## Example Attack Scenarios

Attackers can use SSRF to attack systems protected behind web application firewalls, firewalls, or network ACLs, using scenarios such as:

**Scenario #1:** Port scan internal servers – If the network architecture is unsegmented, attackers can map out internal networks and determine if ports are open or closed on internal servers from connection results or elapsed time to connect or reject SSRF payload connections.

**Scenario #2:** Sensitive data exposure – Attackers can access local files or internal services to gain sensitive information such as `file:///etc/passwd` and `http://localhost:28017/`.

**Scenario #3:** Access metadata storage of cloud services – Most cloud providers have metadata storage such as `http://169.254.169.254/`. An attacker can read the metadata to gain sensitive information.

**Scenario #4:** Compromise internal services – The attacker can abuse internal services to conduct further attacks such as Remote Code Execution (RCE) or Denial of Service (DoS).

**Scenario #5:** AWS Metadata Endpoint (1)
Although SSRF issues may appear to pose a limited risk, attackers can get creative with these vulnerabilities to make requests to non-public URLs that may expose sensitive data.
One such service commonly exploited by attackers in third-party cloud environments is REST-based web services known as cloud metadata endpoints. If configured, a metadata endpoint provides programmatic access to a cloud server’s system configuration, networking details, authentication access keys, etc.