http: web protocol. client make GET request (args in URL), get server response

web page = HTML + CSS (for style, e.g. font) + javascript (programming language to manipulate web pages, very powerful)

to render in browser: HTML parser creates DOM (tree of objects on page), CSS parser embellishes DOM, JS engine runs javascript to manipulate DOM, painter paints DOM onto webpage

- DOM = document object model
- JS engine runs continuously (manipulating DOM when needed)
- javascript can do virtually anything

frames: enables embedding page within a page. neither page can change each other's contents

now: web security

web security is a mess (was added on later)

browsers sandbox javascript, enforce same-origin policy (tabs should be isolated from each other unless same site)

more specifically, same origin policy: one origin should not be able to access resources of another origin

origin = (protocol, hostname, port). all info contained in URL. (if port not listed, there is a default port, but browser will put empty string in origin port). use dumb string matching to compare origins

javascript runs with the origin of the page that loaded it. origin of iframe is the origin of the inner page.

cross-origin communication allowed if both origins agree, use postMessage API, but can't do much with that