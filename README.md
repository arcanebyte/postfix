# Postfix <-> UUCP Mail for the Apple Lisa

The files in this repo are meant to assist the reader with configuring
UUCP on an Apple Lisa running UniPlus+ UNIX System V and Postfix/UUCP on
a Linux host.

## Systems

Apple Lisa 2/5 (with 10MB X/ProFile)  
UniPlus+ UNIX System V (1984)  

Raspberry Pi 3 Model B+  
Ubuntu Server 16.04 LTS (2018)  

## Assumptions

The assumptions here include:

- Ubuntu has a user named `uucp` with a password of `uucp`
- Uniplus has a user named `uucp` with no password

## Examples

Sending mail from the Lisa will require the following syntax:

`mail <uucp_intermediary>!<user>\@<domain>`

The `@` symbol must be escaped or the shell will complain.

```
# mail arcane!james.denton\@outlook.com
Subject: Another test message
This "email" is coming to you from UniPlus+ UNIX for the Apple Lisa.

Hope you enjoy!

James
.
#
```

- A period `.` on a newline will end a message.
- Any headers must be written manually
- The included mail client has no reply function
- Mail will be queued up until UUCP utils run (cron or call)

The UUCP intermediary should accept incoming mail and will copy to the Lisa
on a schedule defined by crontab. Any queued mail on the Lisa will be sent
at that time as well. Nothing is immediate here.
