## OAuth 

- Authorization framework initially developed to solve delegated 
authorization problem 
    - App previously required user password to access information (no scope)
    - Later adopted for simple login, single sign-on across sites, 
    mobile app login (problematic at first)
- Authentication occurs through Open ID Connect 
    - No standard way to get user info in OAuth (no common set of scopes)
    - Almost every implementation of OAuth authentication different 
    (e.g. Google, Facebook)

- Downsides of homegrown auth
    - Responsible for own security and maintenance 

#### OAuth 2.0 terminology 
Core terms: 
- Resource owner - user who owns data 
- Client - application requesting access to database 
- Authorization server - system used to authorize permission 
- Resource server - API or resource server that holds data  
- Authorization grant - proves user has consented to permissions 
- Redirect URI - where user should end up upon success 
- Access token - key used to access requested data on resource server 
    - Authorization code exchanged for access token 
    - Exchange occurs to take advantage of strengths of both front 
    channel and back channel 

More terms:
- Scope - sets of permissions relevant to system 
- Consent - screen presented to user to approve list of scopes 

#### Workflow 
- Front-channel exchanges used to interact w/ user 
    - Info sent to browser limited in security 
- Back-channel exchanges used to send secure data (e.g. access token) 
- Single page apps have limited back-channel  
- Client requests from Auth Server a redirect URI, response type, and scope 
(often includes `openid profile`)

#### Techs 
- Okta away SAML so client only has to deal with OAuth 

#### Sources 
- [OAuth 2.0 and OpenID Connect - Nate Barbettini](https://www.youtube.com/watch?v=996OiexHze0)
