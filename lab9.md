# Lab 9 - Authentication

## Question 0: What authentication scheme is used by default in Django Rest Framework's browsable API? How is this managed?
The browsable API in Django Rest Framework uses session authentication by default. This is managed by having the user login and receive a cookie that the server can refer to retrieve session details between subsequent requests.

## Question 2: What authentication scheme is used by httpie when querying with the -a or --auth option flag?
Basic Authentication is used by httpie -a|--auth.

## Question 3: What is the difference between Session Authentication and Token Authentication? How is Token Authentication an improvement over Basic Authentication?
Session authentication is a stateful, cookies-based authentication method. When a client makes a valid login request, the server saves their session on disk and gives a cookie back to the client. The client cookie allows the session to persist between requests, as the server receives the client cookie and uses the ID to look up their session. The session persists until either the client deletes the cookie, or the server session expires.

Token authentication is a stateless, token-based authentication method. When a client makes a valid login request, the server signs a token using a private key, and gives it to the client. In contrast to Session authentication, all session details are encoded in the payload of the auth token, which gets passed back and forth between the server and client until it expires.

Token authentication is an improvement over Basic authentication for two main reasons. Firstly, it does not require the user to provide their credentials after the initial login request. Secondly, the token signature is a cryptographically secure (e.g. SHA-256) while Basic authentication credentials are not encrypted. This means anyone listening to client traffic could intercept their HTTP requests and obtain the user credentials from the Authentication header. Basic authentication is only secure if the entire request is encrypted via SSL/TLS in the HTTPS scheme.

## Question 4: Provide a high level summary of what happens during an OAuth2 authentication flow. For instance: bitbucket.org > Log In > Log in with Google. What happens when I click "Log in with Google"?
To log into a server using OAuth2 authentication, the auth flow begins with a user clicking a link to log in using a third-party service they have an account with, like Google. The third-party service receives an authorization request, validates it (the resource), and responds to the client with an authorization grant. The grant is then sent by the client to the server. The server validates the authorization grant and responds with an access token. The client can then use the access token for subsequent requests to the server to access resources.

## Question 5: Please provide a link to your code.
https://github.com/dlallan/authentication-lab