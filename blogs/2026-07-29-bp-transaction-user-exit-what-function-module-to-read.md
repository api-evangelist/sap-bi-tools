---
title: "BP transaction user exit: what function module to read current BP data?"
url: "https://community.sap.com/t5/abap-forum/bp-transaction-user-exit-what-function-module-to-read-current-bp-data/m-p/14451828#M1139"
date: "2026-07-29"
author: "Sandra_Rossi"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
I implemented the BAdI BUPA_FURTHER_CHECKS to check data when BP data has been modified by the user, based on the country of the BP and the BP tax numbers that I get by calling respectively the function modules BUA_ADDRESS_GET_ALL and BUP_BUPA_TAX_GET. These function modules work well if I use the role 000000 (General), but BUP_BUPA_TAX_GET returns nothing if I use the role FLCU01 (CVI: FI customer). Why?
