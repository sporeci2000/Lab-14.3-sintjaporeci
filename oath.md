CSRF and the state Parameter
A Cross-Site Request Forgery can happen when a user is tricked into clicking a link that starts a login process without meaning to. An attacker could use this to get an authorization code and access the user’s account.
For example, a user might be logged into a website and receive a seemingly harmless link in an email or message, which secretly initiates the OAuth login flow. 
If the application does not verify the request, the attacker could gain access to sensitive information or perform actions as the user.
The state parameter prevents this by acting like a secret token. When the login process starts, the application creates a random state value. 
This state value is unique for each session and ensures that the OAuth response corresponds to the original request made by the application. After login, the OAuth provider sends it back, and the application checks that it matches. 
If it does not match, the request is blocked. This makes sure that only the original login attempt is accepted and stops attackers from hijacking the process.

Redirect URI Attacks
Sometimes applications accept any URL under a main domain for redirects. For example, if https://example.com is allowed, an attacker could use https://example.com/malicious to get the authorization code. 
The attacker could then exchange it for access to sensitive data. This could include personal information like email addresses, profile details, or connected accounts, which can lead to identity theft or unauthorized actions.
Even small mistakes in redirect validation can create serious security vulnerabilities.
This is like leaving a door open to anyone on the same street. 
A secure approach is to only allow exact, pre-registered URLs so that authorization codes are sent only to trusted locations. 
Developers should avoid wildcards or subdomain allowances unless absolutely necessary and should always double-check that each redirect URI exactly matches the registered value to prevent leaks.

User Experience vs. Security
Adding login options like “Login with GitHub” or “Login with Google” makes signing in much easier because users do not need to create new passwords. 
But this also adds new responsibilities. The application must store and manage access tokens safely and handle potential security risks.
Tokens need to be protected from theft, properly expired when no longer needed, and only used for their intended purpose. 
The development team must also monitor for unusual activity to detect potential breaches.
This is a trade-off between convenience and protection: making login simple for users while making sure sensitive data is safe. 
It is like installing an easy-to-open door;convenient, but it must also be secured properly.

