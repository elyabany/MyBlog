### Ask yourself these questions for the application
   1. What server is running the application?
   2.  Is there a WAF?
   3.  What additional libraries are used? Are there known exploits for these libraries? Custom JS Llbraries?
   4.  Is there Authentication?
        - Username
        - Email
        - OAuth
        - OAuth w/ OpenID Connect
        - SSO
        - MFA
        - Reset Password
        - OTP
    5. What Objects are used?
    6. How is session established?
    - Cookie?
    - Bearer Token?
    - JWT?
    - Is it serialized? (Java, PHP, .NET, Python)
    7. Are there useful comments?
    8. How does it handle special characters?
    9. Can you trigger any error messages?
    - Send malicious characters to every parameter
    - Emojis
    - List of naughty strings (SecLists)
    - Change parameters to array
    EX: [http://example.com/search.php?q[]=test](http://example.com/search.php?q%5B%5D=test)
    10. What common features are present?
    - Edit Profile
    - Email/Messaging
    - File Upload
    - Shopping/Checkout
    - Webhook
    - Flight/Hotel Booking
    - Banking
    11. How is a user identified?
    12. Are there multiple user roles?
    13. Is there an API?
    14. Is there an Content Management System?
    15. Is there a Content Security Policy?
    16. Is CORS implemented?
    17. Is Captcha used?
    18. Are WebSockets used?
    19. Is the source code publicly available?
    
###  Ask yourself these questions about the server hosting the application
    1. What ports are open?
    2. What services are running on those ports?
    3. Is it hosted in the cloud?
        - Check org's ASN #'s
        - Check IP against known AWS/Azure IP ranges
    4. Is it hosting multiple apps using VHosting?
    5. What is the OS?
    6. Can you get the kernel version?
    
    # 
    
### Ask yourself these questions for EVERY page
    1. What part of CRUD?
    2. What HTTP request methods can be used? (GET/POST/PUT/DELETE/etc.)
    3. What parameters can be used?
### Find Chaining Bugs
    1. Open Redirect?
        
        - If yes:
            - Can you redirect to different paths?
            - Can you redirect to different subdomains?
            - Can you redirect to different domains?
    2. Reflected user controlled data?
        - If yes:
            - HTMLi?
            - XSS?
            - SSTI?
    3. CSRF?
    - If yes:
        - What can we do with this endpoint?
        - Is this endpoint an open redirect?
    4. Change HTTP Verb?
    - If yes:
        - Does the endpoint work the same way when the verb is changed?
        - Are any parameters rejected?
###  VULN TESTING DETAILS
    ```
    Account Takeover - Burp (manual)
    Code Injection - Burp (scans/manual)
    HTML Injection - Custom Script (TBD) / Burp (scans/manual)
    IDOR - Burp (manual)
    Information Disclosure - Custom Script (Github_brute-dork) / Manual Search
    Prototype Pollution - Custom Script (Drifting_Embers) / Developer Tools (manual)
    RCE - Nuclei (known CVE) / Burp (manual)
    SSRF - Burp (manual)
    XSS - Custom Script (TBD) / Burp (scans/manual)
    SSTI - Custom Script (TBD) / Burp (scans)
    CSRF - Burp (manual)
    OAuth - Burp (manual)
    De-serialization - Burp (manual/scans) / Source Code Analysis
    HTTP Request Smuggling - Burp (scans)
    WebSockets - Burp (manual)
    HTTP Host Header - Burp (manual)
    ```
###  Recon
    reconftw
    
