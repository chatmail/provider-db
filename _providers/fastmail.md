---
name: Fastmail
status: PREPARATION
domains: 
  - fastmail.com
# Servers list from https://www.fastmail.help/hc/en-us/articles/1500000278342
server:
  - type: imap
    socket: SSL
    hostname: imap.fastmail.com
    port: 993
  - type: smtp
    socket: SSL
    hostname: smtp.fastmail.com
    port: 465
  - type: smtp
    socket: STARTTLS
    hostname: smtp.fastmail.com
    port: 587
before_login_hint: "You must create an app-specific password for Delta Chat before you can log in."
last_checked: 2020-01
website: https://fastmail.com
---

To use Delta Chat with your Fastmail email address
you have to generate a specific password for it.

You can do that in the Fastmail web interface
at "Settings / Import & Setup / Setup Guides / Thunderbird / Next":

- Type in the password shown there into the Delta Chat password field 

Then, click "Next" again and then "Done".

Afterwards you can use Delta Chat as usual.
