#### cookies

cookie: a name, value pair. browser keeps all cookies in a cookie jar. all http GET requests to server will include all cookies for that server. server can set/add cookies with set-cookie in HTTP response

cookies used to track state for an otherwise stateless HTTP protocol

when setting cookies, server specifies cookie scope (domain, path), expiration date, security flags (e.g. only send over HTTPS, can/not be accessed by javascript)

cookie setting rules: domain = any domain suffix of URL, except top level domains (e.g. math.berkeley.edu can set berkeley.edu but not .edu). path = can be anything

- reminder: URL = domain/(path & args)

cookie sending rules: send if path is prefix of URL path, domain is suffix of URL domain

can set, read, delete cookies in javascript (as cookies often used for customization)

cookie policy in somewhat in counter to same-origin policy, which leads to many strange attacks and bypasses of same-origin policy (e.g. cookie jar overflow attack)

#### session

session: a sequence of requests & responses from one browser to one or more sites. authorize user once, all subsequent requests tied to user until session ends

session token: a temporary id for user. often stored in cookie. authenticates user for duration of session

- can also be stored in URL, or in a hidden form field (when filling out a form, a token is sent for that form). most people use a combination of cookies and hidden form fields