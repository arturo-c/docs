---
layout: page
weight: 0
title: Joomla
navigation:
  show: true
---

Joomla supports sending email over SMTP. To have Joomla relay email through SendGrid go to *Site \> Global Configuration* and change:

-   **SMTP Auth** - Yes
-   **SMTP User** - sendgrid\_username
-   **SMTP Pass** - sendgrid\_password
-   **SMTP Host** - smtp.sendgrid.net

The following image shows these settings.

![]({{root_url}}/images/joomla.png)