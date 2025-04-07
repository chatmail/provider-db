# E-mail provider database 

This repository collects information on email providers and their interoperability which is used by the chatmail/core library. 

**The header of the files,** the _front matter_, is included into [chatmail/core](https://github.com/chatmail/core),
to provides them to the [chatmail apps](https://chatmail.at/clients) on the different platforms.
Update is done by setting the desired commit as `REV=`
in [chatmail/core/scripts/create-provider-data-rs.py](https://github.com/chatmail/core/blob/main/scripts/create-provider-data-rs.py) and the run the script.

**The page's content** is built into a web page
that shows the status of the respective provider regarding its usage with chatmail apps,
and details possibly required preparation steps, or explains why the interoperability is broken.


## Format

The files build on this format:

```yaml
---
name: [name of the provider]
status: [OK or PREPARATION or BROKEN]
domains: 
  - an_array
  - of_domains
  - used_by_this_provider
opt:
  max_smtp_rcpt_to: [optional: default is 50]
  strict_tls: [optional: default is true]
server:
  # Repeat the following block for each server (usually one for imap, one for smtp).
  # If no servers are defined, autoconfig, autodiscover or guessing is used;
  # this will lead to the same server-configuration as if there is no provider-entry at all.
  - type: [IMAP or SMTP]
    socket: [SSL or STARTTLS or PLAIN]
    hostname: [hostname to connect to]
    port: [port number]
    username_pattern: [optional: EMAIL or EMAILLOCALPART, default is EMAIL]
before_login_hint: |
  [required for status PREPARATION or BROKEN: a string that will be displayed before the user logs in.
  Multiple lines are possible (line-breaks will be honoured), but keep in mind this text appears within the login form on possibly small displays.
  ]
after_login_hint: |
  [optional: a string that will be displayed in the device chat after the user logged in.
  Multiple lines are possible (line-breaks will be honoured).
  There's more room for text in the device chat than in the login form, but please keep the text concise nonetheless.
  ]
config_defaults:
  # optional, see below for details
  key: value
  other_key: other_value
last_checked: [optional: date when the information was last checked: YYYY-MM]
skip_auto_test: [optional: skip the provider in the automated tests. default is false]
website: [optional: website of the provider]
---
[Markdown-formatted content that gets displayed as provider-page on the web, linked from the apps (if status is not OK)]
```

## Status options

### OK

If the status is `OK`, a standard text is used as page content. You don't need to put in anything.

`before_login_hint` as well as additional content is not available from within the apps for status `OK`.
Use status `PREPARATION` to show `before_login_hint`
or consider using `after_login_hint`, which is shown also for status `OK`.

### PREPARATION

This status means that the user must do some preparing steps
before they can use a chatmail app with their provider.
For example enabling IMAP/SMTP at their provider's settings, or creating an app-specific password.

The required steps must be described as page content in a friendly, helpful howto-style.

Additionally a short, informative sentence must be written as `before_login_hint`, so tech-savy users already know what to do, and others get an idea what to expect from the linked provider page.

### BROKEN

This status means that Chatmail will not work with this provider.

The problems blocking the usage must be summarized as page content in a friendly tone.

Additionally a short, informative sentence must be written as `before_login_hint`, so tech-savy users already know what's up, and others get an idea what to expect from the linked provider page.

**Note:** Bear in mind the `before_login_hint` is displayed by the UIs as normal text, **without** html, markdown, whatever. Therefore, links in the `before_login_hint` are *not allowed*, especially as they tend to be wider than some smartphone displays.


## Configuration Defaults

Beside the server-configuration, chatmail/core has several other options
that can typically be using chatmail apps at runtime.
In most cases the global-default for these options are fine for most providers,
however, if not, you have the possibility to define provider-specific-defaults
with the `config_defaults` section.

The api for that is a bit low-level: you have to define key-value-pairs
where the keys have to match the names used in the API, the values have to be
plain numeric values, see
[Chatmail API](https://c.delta.chat/classdc__context__t.html#aff3b894f6cfca46cab5248fdffdf083d)
for details.

The provider-specific-defaults are applied _once_
after the first successful configuration,
they are not applied later on re-configures or on updates -
reason for that is to respect user-choice of changing these values.


## OAuth2

With the top-level option `oauth2=AUTHORIZER` you can specify,
that emails on the given domains support OAuth2 with the given authorizers.
Supported authorizer is `yandex`.

In contrast to other authorization methods, you cannot use OAuth2
only because the server may support it.
New OAuth2 authorizers require adaptions in chatmail/core
and typically also bureaucratic effort.

### Use OAuth2 together with other options

If for an entered address, OAuth2 is supported,
and the used client supports OAuth2,
the user will be asked if he wants to continue with that.

Only if that is _cancelled_, the `before_login_hint` is shown;
so it is not needed to say sth. about OAuth2 before login.

All other options are applied as usual.


## Limit RCPT TO header

With the `opt` option `max_smtp_rcpt_to: MAX`
you can set the maximum number of recipients
that should be used in an `RCPT TO:` smtp header.
If a message needs to be sent to more recipients,
multiple messages are sent out,
each with exactly the same MIME-message
(with `To:` mime headers that may contain all recipients).

If this limit is not specified, the library picks an reasonable default.


## Strict TLS

By default, all providers in to the provider-database
are assumed to support "Strict TLS".
If that is not true for a specific provider,
you have to add the `opt` option `strict_tls: false`.

Connections with `socket: PLAIN` are not affected by the `strict_tls` option,
it's not ignored, there is just no TLS at all.
