
https://owasp.org/Top10/A03_2021-Injection/

https://www.hackingarticles.in/cross-site-scripting-exploitation/

Kontra lab: https://application.security/free-application-security-training/cross-site-scripting-vulnerability-in-tiktok

1.  Cross-site scripting (XXS) - XSS flaws occur whenever an application includes untrusted data in a new web page without proper validation or escaping, or updates an existing web page with user-supplied data using a browser API that can create HTML or JavaScript. XSS allows attackers to execute scripts in the victim’s browser which can hijack user sessions, deface web sites, or redirect the user to malicious sites.

1.  Attacks:
	session stealing, account takeover, MFA bypass, DOM node replacement or defacement (such as trojan login panels), attacks against the user's browser such as malicious software downloads, key logging, and other client-side attacks
	
2. Mitigation:
	SAST, escaping, whitelist; HTML encoding;<c:out>


## What is cross-site scripting (XSS)?

Cross-site scripting (also known as XSS) is a web security vulnerability that allows an attacker to compromise the interactions that users have with a vulnerable application. It allows an attacker to circumvent the same origin policy, which is designed to segregate different websites from each other. Cross-site scripting vulnerabilities normally allow an attacker to masquerade as a victim user, to carry out any actions that the user is able to perform, and to access any of the user's data. If the victim user has privileged access within the application, then the attacker might be able to gain full control over all of the application's functionality and data.


## What are the types of XSS attacks?

There are three main types of XSS attacks. These are:

-   [Reflected XSS](https://portswigger.net/web-security/cross-site-scripting#reflected-cross-site-scripting), where the malicious script comes from the current HTTP request.
-   [Stored XSS](https://portswigger.net/web-security/cross-site-scripting#stored-cross-site-scripting), where the malicious script comes from the website's database.
-   [DOM-based XSS](https://portswigger.net/web-security/cross-site-scripting#dom-based-cross-site-scripting), where the vulnerability exists in client-side code rather than server-side code.

## How to prevent XSS attacks

Preventing cross-site scripting is trivial in some cases but can be much harder depending on the complexity of the application and the ways it handles user-controllable data.

In general, effectively preventing XSS vulnerabilities is likely to involve a combination of the following measures:

-   **Filter input on arrival.** At the point where user input is received, filter as strictly as possible based on what is expected or valid input.
-   **Encode data on output.** At the point where user-controllable data is output in HTTP responses, encode the output to prevent it from being interpreted as active content. Depending on the output context, this might require applying combinations of HTML, URL, JavaScript, and CSS encoding.
-   **Use appropriate response headers.** To prevent XSS in HTTP responses that aren't intended to contain any HTML or JavaScript, you can use the `Content-Type` and `X-Content-Type-Options` headers to ensure that browsers interpret the responses in the way you intend.
-   **Content Security Policy.** As a last line of defense, you can use Content Security Policy (CSP) to reduce the severity of any XSS vulnerabilities that still occur.


DOM -DOM stands for Document Object Model and is a programming interface for HTML and XML documents. It represents the page so that programs can change the document structure, style and content.

DOM Based XSS is where the JavaScript execution happens directly in the browser without any new pages being loaded or data submitted to backend code. Execution occurs when the website JavaScript code acts on input or user interaction. An example of this could be a website's JavaScript code getting the contents from the window.location.hash parameter and then write that onto the page in the currently being viewed section. The attacker can read and manipulate the document object model (DOM) data to craft a malicious URL. The attacker uses this URL to trick a user into clicking it. If the user clicks the link, the attacker can steal the user’s active session information, keystrokes, and so on. Unlike stored XSS and reflected XSS, the entire DOM-based XSS attack happens on the client browser (i.e., nothing goes back to the server).

Use escapeHTML() to escape all special HTML character.

Use {{ var | escape }} in Django framework HTML encoding