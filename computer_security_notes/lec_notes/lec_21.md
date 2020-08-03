today: cross-site scripting (XSS). attacker injects malicious script into webpage viewed by user (runs in user browser)

idea: attacker tricks server to send malicious script to users (so same origin policy doesn't protect against XSS)

stored XSS: attacker manages to store malicious script at web server, server then unwittingly sends script to user

- samy worm in myspace.com

reflected XSS: script embedded in URL of legit website (remember URL contains the parameters for http request!) server echoes the script back in its response

to defend, can do input validation (whitelist, not blacklist), escape inputs

content-security-policy: have web server provide a whitelist of scripts that user input can contain