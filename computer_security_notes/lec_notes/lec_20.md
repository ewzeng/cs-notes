code injection: browser sends malicious input to server (and server does bad input checking). most common web attack. (similar in spirit to buffer overflow!)

today: SQL injection

web service structure: brower $\leftrightarrow$ web server $\leftrightarrow$ database server (uses SQL)

example: if web server has code: executeQuery("[SQL1]" + input + "[SQL2]"), use input to end [SQL1], execute malicious SQL, then start [SQL2]

- "--" means ignore rest of line

to defend, can disallow special characters, or escape input (add backslashes to every quote from user input, etc.). called sanitizing inputs.

in practice, avoid SQL attacks by using good libraries + frameworks that sanitize inputs, or use parameterized SQL (which defends against all SQL injection attacks)

