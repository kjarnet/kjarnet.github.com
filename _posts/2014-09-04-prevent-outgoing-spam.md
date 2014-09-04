---
layout: post
title: "Prevent outgoing spam"
description: "Preventing outgoing spam from domains using google apps"
category: 
tags: [domain admin, google apps]
---
{% include JB/setup %}

Using DMARC, SPF and DKIM: [support-artikkel på google](https://support.google.com/a/answer/2466580?hl=en&ref_topic=2759254).

1. Add a SPF record to your DNS-setup: 
    * A TXT-record on the root-domain (nothing in the name-column) and this value: `v=spf1 include:_spf.google.com ~all`.
    * You can use `-all` instead of `~all` to enforce a stricter policy, but google warns that this may result in delivery problems.
    * This tells receiving parties that all mail from this domain should origin from google. Other mail-servers can be configured by adding their ip-address as `ip4:address`.
2. Add DKIM signing - this is two steps:
    1. Generate a key using the google apps admin-console, and set up signing of outgoing messages (same dialog).
    2. Add the key to your DNS-setup as a TXT record.
3. Add a DMARC record to your DNS-setup:
    * This tells receiving parties how to treat messages originating from unautorized domains.
    * You can set up quarintining, rejection and logging
    * Example: `v=DMARC1; p=none; rua=mailto:postmaster@your_domain.com`.


