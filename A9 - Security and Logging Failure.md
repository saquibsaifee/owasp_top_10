https://owasp.org/Top10/A09_2021-Security_Logging_and_Monitoring_Failures/

flaw: Auditable events, such as logins, failed logins, and high-value transactions are not logged. • Warnings and errors generate no, inadequate, or unclear log messages. • Logs of applications and APIs are not monitored for suspicious activity. • Logs are only stored locally. • Appropriate alerting thresholds and response escalation processes are not in place or effective.

fix: Ensure all login, access control failures, and server-side input validation failures can be logged with sufficient user context to identify suspicious or malicious accounts, and held for sufficient time to allow delayed forensic analysis. • Ensure that logs are generated in a format that can be easily consumed by a centralized log management solutions. • Ensure high-value transactions have an audit trail with integrity controls to prevent tampering or deletion, such as append-only database tables or similar

## Description

Returning to the OWASP Top 10 2021, this category is to help detect, escalate, and respond to active breaches. Without logging and monitoring, breaches cannot be detected. Insufficient logging, detection, monitoring, and active response occurs any time:

-   Auditable events, such as logins, failed logins, and high-value transactions, are not logged.

-   Warnings and errors generate no, inadequate, or unclear log messages.

-   Logs of applications and APIs are not monitored for suspicious activity.

-   Logs are only stored locally.

-   Appropriate alerting thresholds and response escalation processes are not in place or effective.

-   Penetration testing and scans by dynamic application security testing (DAST) tools (such as OWASP ZAP) do not trigger alerts.

-   The application cannot detect, escalate, or alert for active attacks in real-time or near real-time.

## How to Prevent

Developers should implement some or all the following controls, depending on the risk of the application:

-   Ensure all login, access control, and server-side input validation failures can be logged with sufficient user context to identify suspicious or malicious accounts and held for enough time to allow delayed forensic analysis.
    
-   Ensure that logs are generated in a format that log management solutions can easily consume.
    
-   Ensure log data is encoded correctly to prevent injections or attacks on the logging or monitoring systems.
    
-   Ensure high-value transactions have an audit trail with integrity controls to prevent tampering or deletion, such as append-only database tables or similar.
    
-   DevSecOps teams should establish effective monitoring and alerting such that suspicious activities are detected and responded to quickly.
    
-   Establish or adopt an incident response and recovery plan, such as National Institute of Standards and Technology (NIST) 800-61r2 or later.


## Example Attack Scenarios

**Scenario #1:** A children's health plan provider's website operator couldn't detect a breach due to a lack of monitoring and logging. An external party informed the health plan provider that an attacker had accessed and modified thousands of sensitive health records of more than 3.5 million children. A post-incident review found that the website developers had not addressed significant vulnerabilities. As there was no logging or monitoring of the system, the data breach could have been in progress since 2013, a period of more than seven years.

**Scenario #2:** A major Indian airline had a data breach involving more than ten years' worth of personal data of millions of passengers, including passport and credit card data. The data breach occurred at a third-party cloud hosting provider, who notified the airline of the breach after some time.

**Scenario #3:** A major European airline suffered a GDPR reportable breach. The breach was reportedly caused by payment application security vulnerabilities exploited by attackers, who harvested more than 400,000 customer payment records. The airline was fined 20 million pounds as a result by the privacy regulator.