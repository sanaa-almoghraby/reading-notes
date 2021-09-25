# What is OAuth
### 1.What is OAuth?

OAuth is an open-standard authorization protocol or framework that describes how unrelated servers and services can safely allow authenticated access to their assets without actually sharing the initial, related, single logon credential. In authentication parlance, this is known as secure, third-party, user-agent, delegated authorization.

### 2.Give an example of what using OAuth would look like.
 when you go to log onto a website and it offers one or more opportunities to log on using another website’s/service’s logon. You then click on the button linked to the other website, the other website authenticates you, and the website you were originally connecting to logs you on itself afterward using permission gained from the second website.
### 3.How does OAuth work? What are the steps that it takes to authenticate the user?
The following happens (greatly simplified):

1.The first website connects to the second website on behalf of the user, using OAuth, providing the user’s verified identity.
2.The second site generates a one-time token and a one-time secret unique to the transaction and parties involved.
3.The first site gives this token and secret to the initiating user’s client software.
4.The client’s software presents the request token and secret to their authorization provider (which may or may not be the second site).
5.If not already authenticated to the authorization provider, the client may be asked to authenticate. After authentication, the client is asked to approve the authorization transaction to the second website.
6.The user approves (or their software silently approves) a particular transaction type at the first website.
7.The user is given an approved access token (notice it’s no longer a request token).
8.The user gives the approved access token to the first website.
9.The first website gives the access token to the second website as proof of authentication on behalf of the user.
10.The second website lets the first website access their site on behalf of the user.
11.The user sees a successfully completed transaction occurring.
12.OAuth is not the first authentication/authorization system to work this way on behalf of the end-user. In fact, many authentication systems, notably Kerberos, work similarly. What is special about OAuth is its ability to work across the web and its wide adoption. It succeeded with adoption rates where previous attempts failed (for various reasons).
### 4.What is OpenID?
, OpenID is about authentication: as a commenter on StackOverflow pithily put it: "OpenID is for humans logging into machines, OAuth is for machines logging into machines on behalf of humans."

OpenID would serve as a single sign-in, vouching for the identities of users. But in practice OpenID was difficult to implement on the developer side, and never really became that appealing to users,
![](https://www.okta.com/sites/default/files/styles/1640w_scaled/public/media/image/2020-10/Authentication_vs_Authorization.png?itok=uBFRCfww)

# Authorization and Authentication flows

### 1.What is the difference between authorization and authentication?
![](https://miro.medium.com/max/1000/0*2k5bWdBNXH_cOfx_.png)
### 2.What is Authorization Code Flow?
is used to obtain an access token to authorize API requests. ... Access tokens, obtained using authorization code flow, provide permissions for your application to manipulate documents and other resources on behalf of a Mendeley user and make requests for all API resources.
![](https://developer.accela.com/docs/graphics/login_flow.png)
### 3.What is Authorization Code Flow with Proof Key for Code Exchange (PKCE)?
The Authorization Code Flow + PKCE is an OpenId Connect flow specifically designed to authenticate native or mobile application users. This flow is considered best practice when using Single Page Apps (SPA) or Mobile Apps. PKCE, pronounced “pixy” is an acronym for Proof Key for Code Exchange.
### 4.What is Implicit Flow with Form Post?
As an alternative to the Authorization Code Flow, OAuth 2.0 provides the Implicit Flow, which is intended for Public Clients, or applications which are unable to securely store Client Secrets. While this is no longer considered a best practice for requesting Access Tokens, when used with Form Post response mode, it does offer a streamlined workflow if the application needs only an ID token to perform user authentication.


### 5.What is Client Credentials Flow?
With machine-to-machine (M2M) applications, such as CLIs, daemons, or services running on your back-end, the system authenticates and authorizes the app rather than a user. For this scenario, typical authentication schemes like username + password or social logins don't make sense. Instead, M2M apps use the Client Credentials Flow (defined in OAuth 2.0 RFC 6749, section 4.4).
The Client Credentials flow is a server to server flow. There is no user authentication involved in the process. ... This flow is useful for systems that need to perform API operations when no user is present. It can be nightly operations, or other that involve contacting OAuth protected APIs.
![](https://apaleo.dev/assets/images/oauth/client_credentials_flow.png)
### 6.What is Device Authorization Flow?
With input-constrained devices that connect to the internet, rather than authenticate the user directly, the device asks the user to go to a link on their computer or smartphone and authorize the device. This avoids a poor user experience for devices that do not have an easy way to enter text. To do this, device apps use the Device Authorization Flow (drafted in OAuth 2.0). For use with mobile/native applications.


### 7.What is Resource Owner Password Flow?
Though we do not recommend it, highly-trusted applications can use the Resource Owner Password Flow, which requests that users provide credentials (username and password), typically using an interactive form. The Resource Owner Password Flow should only be used when redirect-based flows (like the Authorization Code Flow) cannot be used.
### The Resource Owner Password Credentials flow allows exchanging the username and password of a user for an access token and, optionally, a refresh token. The primary difference is that the user's password is accessible to the application. ...
![](https://www.oreilly.com/library/view/getting-started-with/9781449317843/httpatomoreillycomsourceoreillyimages986441.png)

