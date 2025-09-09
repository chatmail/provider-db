---
name: Yahoo
status: PREPARATION
domains: 
  - yahoo.com
  - yahoo.de
  - yahoo.it
  - yahoo.fr
  - yahoo.es
  - yahoo.se
  - yahoo.co.uk
  - yahoo.co.nz
  - yahoo.com.au
  - yahoo.com.ar
  - yahoo.com.br
  - yahoo.com.mx
  - myyahoo.com
  - ymail.com
  - rocketmail.com
  - yahoodns.net
server:
  - type: imap
    socket: SSL
    hostname: imap.mail.yahoo.com
    port: 993
  - type: smtp
    socket: SSL
    hostname: smtp.mail.yahoo.com
    port: 465
before_login_hint: To use your Yahoo email address you have to create an app password in the Yahoo account security screen.
last_checked: 2025-09
website: https://www.yahoo.com
---

To use your Yahoo email address you have to create an app password in the [Yahoo account security screen](https://login.yahoo.com/account/security). There you will find a setting titled "Generate app password". Please use it to generate an app password. Then enter the generated password in the app.
