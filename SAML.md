## SAML 

#### Background 
- Security Assertion Markup Language - federated protocol 
- XML-based
- Managing access control for a group of users and a group of different applications 
- Past situtation: 
    - Separate user databases for each app 
    - Have to track multiple usernames and passwords w/ separate policies and expirations
    - Admins and ISVs must keep track of when app users need to have access to certain apps revoked 
    - Enterprise apps no longer running within single company network, but moving towards cloud w/ increased collaboration 

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
- Benefits: streamlined experience for client, SP's user database load reduced 
- Both IdP and SP can be configured on a single BIG-IP via APM
- Note: 
    1. SP never directly interacts with IP. Browser acts as agend to carry out all redirections 
    2. SP needs to know which IdP to redirect to before it can know who user is 
    3. SP can't know who the user is until the SAML assertion comes back from IP 
    4. Flow doesn't have to start from SP. IdP can also initiate authentication flow 
    5. SAML authentication flow is asynchronous. SP doesn't maintain any state of authentication requests generated. IdP responses must contain all necessary info 
        - RelayState - HTTP parameter included in SAML request and response. Provides info about state of request 

#### Misc terminology 
- LDAP - lightweight data access protocol 
- ISV - independent software vendor 

### Implementation Roadmap 
1. Understanding the role of a Service Provider
2. Single IdP v. Multiple IdPs
3. Understanding SP-initiated Login Flow 
4. Exposing SAML configuration in SP 
5. Enabling SAML for everyone v. a subset of users 
6. Implementing a "backdoor"

#### Understanding the role of a Service Provider


#### Single IdP v. Multiple IdPs

#### Exposing SAML configuration in SP 


#### Enabling SAML for everyone v. a subset of users 

#### Implementing a "backdoor"

#### Sources 
- [Okta SAML documentation](https://www.okta.com/integrate/documentation/saml/)