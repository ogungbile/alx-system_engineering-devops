# Postmortem Report

## 505 Error While sending an email

<p align="center">
<img src="https://github.com/ogungbile/alx-system_engineering-devops/blob/master/0x19-postmortem/email_error_01.jpg?raw=true" width=100% height=100% />
</p>

### Incident report for Email failed to send

#### Summary

On February 24, 2023 at noon, users encountered issues with outgoing mails as they were rejected by the recipients mail server.

#### Timeline

- 12:00  -550 Error for anyone trying to send mail
- 12:01  -Ensuring configuration settings on the mail client(outlook) is correct. 
- 12:04  -Telnet to the mail server(mail.cobranet.ng) on port 587 and 25 failed to connect
- 12:07  -Pings and nslookup to the mail server resolved to the same IP address(80.89.176.226)
- 12:10  -under blacklist tab on mxtoolbox.com, the client IP address was observed to be blacklisted(RATS)
- 12:14  -The client public address was changed to a new one to fix issue and client was advised to follow up with their host in order to whitelist the old IP. Users were further advised to scan their computer systems with anti malware program in order to forestall a re-occurrence.
- 12:20 ** -Users ran anti-malware scan on all of their systems
- 12:23 ** -Users can send out mails successfully 


#### Root Cause and Resolution

Blocks occur when a mail server IP address is added to a blocklist (or blacklist) primarily because of sending violations such as the IP or domain was used by spammers to send bulk or spam emails. In other words, the sender server was considered as a source of spam. Blocks may also take place if the message content is flagged by a filter on the receiving server. Another reason might be due to authentication error when login credentials of a mail client does not match. The public IP address of the sender was changed to resolve issue

#### Corrective and Preventive Measures

- Users were advised to scan all their systems with anti-malware program and follow up with their mail host to whitelist the former IP that was blocked
