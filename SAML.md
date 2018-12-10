## SAML 

- Security Assertion Markup Language 
- Managing access control for a group of users and a group of different applications 
- Past situtation: 
    - Separate user databases for each app 
    - Have to track multiple usernames and passwords 

#### Components 
- User 
- IdP (identity provider) 
- SP (service provider)

#### Workflow 
- Client hits SP. If client authenticated, services provided. If not, SP passes client 
on to IdP. 
- If IdP recognizes client as authorized, creates an `Assertion` object (XML based), 
containing user information (e.g. company, username, department, etc.)
- `Assertion` used by all included SP's 

#### Details 
- Benefits: streamlined experience for client, SP's user database load reduced \
- Both IdP and SP can be configured on a single BIG-IP via APM