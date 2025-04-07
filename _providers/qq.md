---
name: QQ Mail
status: PREPARATION
domains:
- qq.com
- foxmail.com
server:
  - type: imap
    socket: SSL
    hostname: imap.qq.com
    port: 993
    username_pattern: emaillocalpart
  - type: smtp
    socket: SSL
    hostname: smtp.qq.com
    port: 465
before_login_hint: "Manually enabling IMAP/SMTP and creating an app-specific password are required."
last_checked: 2021-06
website: https://mail.qq.com/
---

To use your QQ Mail address, [manually enabling IMAP/SMTP and creating an app-specific password](https://service.mail.qq.com/cgi-bin/help?subtype=1&id=28&no=331) are required.

