## Cross-site Request Forgery  

#### Problem details 
- CSRF/XSRF 
- Type: confused deputy ("privilege escalation")
- Hijacks inherent browser functionality of automatically sending all cookies to any site 
that user currently has cookie for, as well as aspects of HTTP specification 
- Considered third big web attack after cross-site scripting and SQL injection 
- Ex: comment button (or even onload) of malicious page sends fund transfer request via 
the session token of a banking page open in another tab 
- Attacker usually can't see response data, so used for state-changing requests and not reads
    - Attacker can read if site also vulnerable to XSS 

#### Problem origin 
- Session persistence via cookies 
    - Session ID stored on server, client sends cookies 
    - Use HTTP only flag to avoid XSS attacks (prevents cookie from being modified)
    - Still vulnerable to CSRF 
    - Alt: store session info on client side 
        - Not vulnerable to CSRF (specific to cookies)
        - Vulnerable to XSS
- Relaxed origin policies 
    - CORS (Cross Origin Resource Sharing) recengtly handles XHR's (XML HTTP Requests)
    - XHR's previously followed same-origin policy 

#### Solutions: 
    - Premise: need to verify where the request is coming from 
    - Past: referrer header in links
        - Problem: header not always sent in the correct way, or can be blocked by privacy 
        software, adblockers, or proxies 
    - Re-authentication 
        - e.g. captcha, password 
    - CSRF token: random token provided with form and required to be sent back by user 
        - Refreshed regularly or with every request 
        - Included both in cookie header and request body 
        - Attacker can't access code running in the browser, even if can access cookie 
        (exception: XSS vulnerability) 
    - Use libraries with built-in CSRF protection 