#### CSRF

CSRF: cross site request forgery attack

HTML forms: allows user to provide some data. when submit, browser send HTTP POST request. used everywhere. as always, browser attaches cookies

CSRF attack: suppose user visiting both bank.com, evil.com. evil.com has a link to bank.com with certain args in URL. user clicks link, sends request to bank.com and attaches current bank.com cookies (which are valid). thus evil.com makes user do something the user doesn't want

- the user doesn't even need to click link. evil.com can have a HTML form + javascript that sends it as soon as it loads

to defend, can use CSRF tokens: add secret token into webpage forms (as a already filled-in hidden field). then form submitted, verify hidden field. thus only forms embedded in the webpage create valid HTTP posts

can also do referer validation: when issue a HTTP request, include referer header that indicates which webpage initiated the request. (not fool proof, but good simple check)

- referer header is set by user browser, but some browsers strip the referer header for privacy