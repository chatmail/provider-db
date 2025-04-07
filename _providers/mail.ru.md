---
name: Mail.ru
status: PREPARATION
domains:
- mail.ru
- inbox.ru
- internet.ru
- bk.ru
- list.ru
# For vk.com see designated file, ./vk.com.md
server:
  - type: imap
    socket: SSL
    hostname: imap.mail.ru
    port: 993
  - type: smtp
    socket: SSL
    hostname: smtp.mail.ru
    port: 465
before_login_hint: Вам необходимо сгенерировать "пароль для внешнего приложения" в веб-интерфейсе mail.ru, чтобы mail.ru работал с chatmail.
last_checked: 2021-07
website: https://mail.ru/
---

См. <https://help.mail.ru/mail/security/protection/external> для получения
дополнительной информации о том, как сгенерировать такой внешний пароль для
chatmail.

