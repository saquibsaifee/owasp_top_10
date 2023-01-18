https://application.security/free-application-security-training/understanding-apache-log4j-vulnerability

**Remote Code Execution** vulnerability reported in **Apache's** `log4j` package, a popular logging library used by developers for **debugging** or **tracing** events in **Java** applications. 

A **malicious actor** can exploit this vulnerability to load arbitrary Java objects, which may result in executing **unauthorized commands** or **actions** on the vulnerable system.

**Vulnerability:** JNDI(Java Naming and Directory Interface) Lookup

**Fix**: update the version of your **Apache log4j** library to `2.16.0`

Exploit GitHub: https://github.com/welk1n/JNDI-Injection-Exploit

Log4j CVE: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-45046


The `log4j` library supports by default a logging feature called **Lookups** or **Lookup Plugins**, which allows injecting dynamically generated information into log strings.

For example, passing the **lookup expression** `${java:version}` to a `log.info()` method will output the **Java runtime version** in the logging message.

In **2013**, the `log4j` package added a new **Lookup plugin** called **JNDI Lookup**. This plugin uses Java's **JNDI** (**Java Naming and Directory Interface**) API, which allows an application to load **java objects** remotely from an **LDAP server** or an **RMI registry**.

The syntax for **Log4j's** **JNDI Lookup** plugin is:
`${jndi:ldap://hostname/objectpath}`

