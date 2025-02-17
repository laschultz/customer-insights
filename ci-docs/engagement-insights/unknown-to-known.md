---
title: Recognize web events from previously authenticated visitors with unknown to known
description: The unknown to known feature allows you to associate events on a website with visitors who authenticated previously. 
ms.reviewer: mhart
ms.author: mkisel
author: mkisel11
ms.date: 7/15/2021
ms.service: customer-insights
ms.subservice: engagement-insights 
ms.topic: overview
ms.manager: shellyha
---
# Recognize web events from previously authenticated visitors

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

The **unknown to known** feature in the engagement insights capability enables associating events on a website with visitors who authenticated previously. If the feature is disabled, visitors who authenticated during an earlier visit and then left are not identified if they don’t authenticate again when coming back. 

For example, a person visited a website last week, signed into their user account on the site, and browsed the product catalog. The person returns the following week to browse more products without signing into their account. The site owner using the **unknown to known** feature would know that the same person had returned and what they had done on the site. This allows for more precise reporting and analysis of website activities.

## Enable unknown to known

You need to be a [workspace admin](user-roles.md) to enable this feature. 

1. In engagement insights, go to **Admin** > **Workspace**. 
2. Select the **Settings** tab.
3. In the **Unknown to known** section, set the toggle to **Enabled**.

![Enable unknown to known](media/U2Ktoggle.png "Enable unknown to known")

## Adding JavaScript code to your site's tracking snippet

A website can capture **user authId** with the following JavaScript sample using the [engagement insights web SDK](advanced-SDK-implementation.md). In order for **unknown to known** feature to work, you need to capture authId *and* enable userMapping:True in your JavaScript snippet as in the sample below.

```
[…]
window, document
{
src:"https://download.pi.dynamics.com/sdk/web/mspi-0.min.js",
name:"myproject",
cfg:{
ingestionKey:<paste your ingestion key>",
autoCapture:{
view:true,
click:true
},
userMapping: true
},
user:{
authId: getLoggedInUserId()*,
email: getLoggedInUserEmail()*,
authType: "MSA",
name: "Alex Jensen"
}
[…]
```

[!INCLUDE[footer-include](../includes/footer-banner.md)]
