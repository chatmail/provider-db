---
name: Aol. (America Online)
domains: 
  - aol.com
status: PREPARATION
server:
  - type: imap
    socket: SSL
    hostname: imap.aol.com
    port: 993
  - type: smtp
    socket: SSL
    hostname: smtp.aol.com
    port: 465
before_login_hint: To log in to AOL, you need to set up an app password in the AOL web interface.
last_checked: 2020-02
website: https://aol.com
---

To enable using AOL, you have to turn on some extra settings:

1. Log into AOL on the web and navigate to [Account Info > Account Security](https://login.aol.com/account/security)
2. If two-step verification is set to "ON:"
  * Temporarily turn *two-step verification* to *OFF* (you may turn this back after the account is set up in the client).
  * On the left navigation panel, click *Personal Info*, then click back to *Account Security* to refresh the page.
3. Select *Manage app passwords*, then from the Select your app pulldown, select "Other App."
4. In the text field labeled Enter any name, then click the *Generate* button.
5. Copy the password provided as you will need this in the client. If you write it down manually, leave out the spaces.

