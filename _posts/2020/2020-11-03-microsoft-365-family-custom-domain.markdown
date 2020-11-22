---
layout: post
title:  "Using Custom Domain with Microsoft 365 Family"
date:   2020-11-03 00:00:00 +0000
categories: 
---

I recently bought a subscription to Microsoft 365 Family. I already have a domain (ratana.info) that I would like to use. However it appeared that Microsoft was pushing hard for users to register their domains with GoDaddy. There was no directly way to connect your domain from a different registrar.

After searching around, I came across this [Reddit post](https://www.reddit.com/r/Office365/comments/cmk120/use_office365_personal_with_your_own_domain_no/) which showed how it can be done. Here’s the cleaned up steps.

## Step 1 Find your mxRecordValue

1. Log into outlook.com
1. On the top right menu bar, click on the Diamond icon (Manage Premium). This will pop up a Settings window.
1. Under "Premium" -> "Personalized email address", click to add a domain
1. Follow through until a new window pops up with GoDaddy page
1. Note the URL. It should be something like this: 
`https://domainconnect.godaddy.com/v2/domainTemplates/providers/outlook.com/services/personalizedoutlookemail/apply?mxRecordValue=111111111&state=xxxxxxxxx&redirect_url=https%3A%2F%2Foutlook.live.com/mail/LaunchDomainConnectNextStep.html
`
1. Note the `mxRecordValue` and the number after
1. Close the window

## Step 2 Add DNS records

1. Log into your registrar
1. Add the following DNS records
```
Type   Name            Value
----------------------------------------------------------
CNAME  autodiscover    autodiscover.outlook.com
CNAME  _domainconnect  _domainconnect.gd.domaincontrol.com
TXT    @               v=spf1 include:outlook.com
TXT    _outlook        111111111
MX     @               111111111.pamx1.hotmail.com
```
1. Replace 111111111 with the `mxRecordValue`'s value from Step 1

## Step 3 Add customized address

1. Wait a few minutes for the DNS records to propagate
1. Log into outlook.com
1. On the top right menu bar, click on the Diamond icon (Manage Premium).
1. Under "Premium" -> "Personalized email address", your domain should be linked.
1. Add a new customized address.

## Step 4 Set custom address as default From

1. Log into outlook.com
1. On the top right menu bar, click on the Diamond icon (Manage Premium).
1. Under "Mail" -> "Sync email" -> "Set default From address, select your new custom address