
https://owasp.org/Top10/A01_2021-Broken_Access_Control/

Broken Access Control - Restrictions on what authenticated users are allowed to do are often not properly enforced. Attackers can exploit these flaws to access unauthorized functionality and/or data, such as access other users' accounts, view sensitive files, modify other users’ data, change access rights, etc.

Attacks: LFI, IDOR, Path Traversal

Mitigation: Role-based access, disable default director listing, no backups, log access control


## How to Prevent

Access control is only effective in trusted server-side code or server-less API, where the attacker cannot modify the access control check or metadata.

-   Except for public resources, deny by default.
    
-   Implement access control mechanisms once and re-use them throughout the application, including minimizing Cross-Origin Resource Sharing (CORS) usage.
    
-   Model access controls should enforce record ownership rather than accepting that the user can create, read, update, or delete any record.
    
-   Unique application business limit requirements should be enforced by domain models.
    
-   Disable web server directory listing and ensure file metadata (e.g., .git) and backup files are not present within web roots.
    
-   Log access control failures, alert admins when appropriate (e.g., repeated failures).
    
-   Rate limit API and controller access to minimize the harm from automated attack tooling.
    
-   Stateful session identifiers should be invalidated on the server after logout. Stateless JWT tokens should rather be short-lived so that the window of opportunity for an attacker is minimized. For longer lived JWTs it's highly recommended to follow the OAuth standards to revoke access.


## Example Attack Scenarios

**Scenario #1:** The application uses unverified data in a SQL call that is accessing account information:

 `pstmt.setString(1, request.getParameter("acct"));  ResultSet results = pstmt.executeQuery( );`

An attacker simply modifies the browser's 'acct' parameter to send whatever account number they want. If not correctly verified, the attacker can access any user's account.

 `https://example.com/app/accountInfo?acct=notmyacct`

**Scenario #2:** An attacker simply forces browses to target URLs. Admin rights are required for access to the admin page.

 `https://example.com/app/getappInfo  https://example.com/app/admin_getappInfo`

If an unauthenticated user can access either page, it's a flaw. If a non-admin can access the admin page, this is a flaw.
