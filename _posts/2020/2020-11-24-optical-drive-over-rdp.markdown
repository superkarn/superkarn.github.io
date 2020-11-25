---
layout: post
title:  "Optical Drive Over RDP"
date:   2020-11-24 00:00:00 +0000
categories: 
---

I ran into an issue trying to access an optical drive (Bluray) on a Windows 10 machine via a Remote Desktop Session.  The drive would not show up in the app.  After searching, I found this [post](https://social.technet.microsoft.com/Forums/office/en-US/1b486631-324e-48fd-8b40-efff1d17a892/controlling-cddvd-over-remote-desktop-connection?forum=w7itpromedia) from 2010. 

The solution is to enable the policy "All Remove Storage: Allow direct in remote sessions".  You can do so by following these steps.

1. Open "Local Group Policy Editor"
1. Under "Local Computer Policy" (left panel), navigate down to
  - Computer Configuration
  - Administrative Templates
  - System
  - Removable Storage Access
1. In the right panel, enable the setting "All Remove Storage: Allow direct in remote sessions"
1. You should have now have access