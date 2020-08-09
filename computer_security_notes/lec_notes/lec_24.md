#### Impersonation Attacks

user authenticates server w/ certificates, server authenticates user thru login (usually)

3 basic types of auth: something you know, you have, you are. two-factor auth: use different types of auth (e.g. password and fingerprint). so password & security question is not two-factor

session hijacking attack: on-path attacker steal sessionID cookie. to defend: use https. should also set cookie to secure (sent only over https), so attacker cannot provide a http link. should also set to httpOnly (no javascript)

phishing attack: create a fake website that appears similar to the real one but on different domain (and obtain valid certificate for that domain). then trick user to visit site and input sensitive data

- to defend: check URL in address bar
- URL obfuscation attack (choose similarly looking URL with typo). homeograph attack: use weird unicode (e.g. cyrillic p)

spear phishing: targeted phishing that includes details that seemingly must mean it's legitimate (very effective)

#### UI Attacks

clickjacking attack: user's mouse click used in a way not intended by user. e.g. evil site frames good site, but puts UI on top of parts of the inner frame, so inner site looks different. can trick user to do unintended things on good site

temporal clickjacking: tell user to double click. after first click, sensitive button appears. user then clicks it by mistake with the second click

cursorjacking: javascript displays a shifted cursor and hope user doesn't see real cursor (can make fake cursor much more eye-catching). can make user click things in an iframe/brower dialogue box without noticing

to defend: 

- good site asks for user confirmation (but bad user experience), UI randomization (but websites will look strange), framebusting (prevent other pages from framing it, very common, but easy to have bugs)

- browser can freeze screen outside of iframe when real pointer enters iframe + lightbox effect around pointer to prevent cursorjacking. brower can also implement UI delay to defend temporal clickjacking

- X-Frames-Option: web tells brower in HTTP header not to be framed, but most sites don't use it (because sites want to be framed by friend sites, and thus write their own more flexible framebusting code)

browser-in-brower attack: attacker.com draws a browser, tricks user in thinking that it is a real browser window overlayed on top of attacker.com browser window