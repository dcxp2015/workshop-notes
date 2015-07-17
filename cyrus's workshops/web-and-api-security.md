# Web and API Security

### What is Web Security
- Protecting online applications against attack
- Preventing exfiltration of data after a breach

### Why is it common?
- Security is hard
- Attackers only need a single hole, defenders need to close every hole
- Physical security is also an unsolved problem!

## OWASP Top 10

#### Injection
- Allowing malicious data to impact code that is run
- SQL Injection is a primary example
    - SQL code is influenced by user
    - Usually happens when SQL query is directly concatenated with data
    - Easy to avoid: use parameterized queries and prepared statements
- Mass Assignment
    - Taking all the data from form and creating dynamic query
    - Exposed by ORM functionality used in web frameworks
    - Make sure to whitelist fields that will be updated
    - GitHub pwned

#### Broken Authentication and Session Management
- Handle the session token with care
    - Don't store it in the URL
    - Make sure to assign a new one after the user logs in
    - Delete it after the user logs out
    - Session timeouts
- Passwords
    - Store passwords with a computationally intensive hash (bcrypt, scrypt, etc)
    - The slower the better
    - Don't attempt to create your own version
    - Avoid MD5 or SHA1; they are both too fast and somewhat broken

#### Cross-site Scripting (XSS)
- User input is able to execute in the browser
- Not properly escaped
- Reflected: directly from the URL vs. Stored: Pulled from server database and put onto the page
- Different types of XSS
    - HTML XSS: Use script tags to insert the JavaScript you want
    - JS XSS: Directly in JavaScript already
    - JSON XSS: Rarer but cool, usually when JSON is dumped directly onto the page

#### Insecure Direct Object Reference
- User directly access a page they shouldn't be able to (ex: /profile/1 to /profile/1337 just by changing the URL)
- Avoid predictable URLs (like increasing IDs) if possible
- Make sure to double check that a user can access the page on every page

#### Security Misconfiguration
- Frameworks or servers used aren't configured in a secure way
- Usually simple to avoid: read all documentation and pay special attention to configuration settings
- Easy to overlook since there's usually no obvious error when configuration is insecure

#### Sensitive Data Exposure
- Allowing important information to be left unsecured or improperly secured
- Usually means poorly configured SSL/HTTPS
- Double-check what is transmitted unencrypted and what ends up being encrypted!

#### Missing Function Level ACL
- Avoid "security through obscurity"
    - Hiding something or making it unpredictable is not the same as protecting it
- Even actions that the user "could never find" should be protected

#### Cross-site Request Forgery (CSRF)
- Forcing the user's browser to perform a malicious action
- Basic case is a link that has side effects
    - ex: browsing to a bank's transfer page automatically transfers the money
- Use a CSRF token to prevent these attacks
    - Useful library for Node/Express: [here](https://github.com/expressjs/csurf)

#### Using Components with Known Vulnerabilities
- Older versions of libraries and frameworks will often have well known published vulnerabilities
- Always use the most up-to-date version of a library your code can handle
- For Node, npm can help with managing versions (package.json)

#### Insecure Redirects
- Malicious attackers can use your websites redirect (usually redirecting after login) to go to a malicious website
- Base domain is yours and looks trustworthy (ex: google.com) but the redirect portion will take them to another website
- To avoid: perform whitelisting on the domains that can be redirected to, or don't redirect based on URL alone

### Useful Tools
- [SSL Labs](https://www.ssllabs.com/)
- [Node Security](https://nodesecurity.io)
- npm shrinkwrap
- [retire.js](http://bekk.github.io/retire.js/)
- [helmetjs](https://github.com/helmetjs/helmet)
- [csurf](https://github.com/expressjs/csurf)

## Key Takeways
- Never trust the user
- Double-check everything
- Being compromised is eventually inevitable, so prepare for how you will recover
- Server-side checking is gold; client-side checking is for quick validation only
- Security and UX should go hand-in-hand
