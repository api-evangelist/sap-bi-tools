---
title: "Processing Issue - Program RVV50R10C"
url: "https://community.sap.com/t5/abap-forum/processing-issue-program-rvv50r10c/m-p/14504929#M1361"
date: "2026-10-15"
author: "akshat_ra"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
Hi, We have a background job scheduled for program RVV50R10C every 15 mins in PROD to create the outbound deliveries with a custom variant . There is custom logic implemented in USEREXIT_SAVE_DOCUMENT in include MV50AFZ1 which MODIFY a Z DB table entry for the delivery. The same variant is available in quality and other systems.
