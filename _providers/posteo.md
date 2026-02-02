---
name: Posteo
status: PREPARATION
domains:
  - posteo.de
  - posteo.af
  - posteo.at
  - posteo.be
  - posteo.ca
  - posteo.ch
  - posteo.cl
  - posteo.co
  - posteo.co.uk
  - posteo.com
  - posteo.com.br
  - posteo.cr
  - posteo.cz
  - posteo.dk
  - posteo.ee
  - posteo.es
  - posteo.eu
  - posteo.fi
  - posteo.gl
  - posteo.gr
  - posteo.hn
  - posteo.hr
  - posteo.hu
  - posteo.ie
  - posteo.in
  - posteo.is
  - posteo.it
  - posteo.jp
  - posteo.la
  - posteo.li
  - posteo.lt
  - posteo.lu
  - posteo.me
  - posteo.mx
  - posteo.my
  - posteo.net
  - posteo.nl
  - posteo.no
  - posteo.nz
  - posteo.org
  - posteo.pe
  - posteo.pl
  - posteo.pm
  - posteo.pt
  - posteo.ro
  - posteo.ru
  - posteo.se
  - posteo.sg
  - posteo.si
  - posteo.tn
  - posteo.uk
  - posteo.us
server:
- hostname: posteo.de
  port: 993
  socket: SSL
  type: imap
- hostname: posteo.de
  port: 143
  socket: STARTTLS
  type: imap
- hostname: posteo.de
  port: 465
  socket: SSL
  type: smtp
- hostname: posteo.de
  port: 587
  socket: STARTTLS
  type: smtp
before_login_hint: "You must create an app-specific password before you can log in."
last_checked: 2026-01
website: https://posteo.de/
---

To use your Fastmail email address you have to generate a specific password for it.
Here is a guide on how to do that (also in German and Spanish):
<https://posteo.de/en/help/app-passwords>
