---
name: nauta.cu
domains:
  - nauta.cu
status: OK
opt:
  max_smtp_rcpt_to: 20
  strict_tls: false
server:
  - type: imap
    socket: STARTTLS
    hostname: imap.nauta.cu
    port: 143
  - type: smtp
    socket: STARTTLS
    hostname: smtp.nauta.cu
    port: 25
config_defaults:
  media_quality: 1
last_checked: 2024-01
skip_auto_test: true
website: https://webmail.nauta.cu
---

