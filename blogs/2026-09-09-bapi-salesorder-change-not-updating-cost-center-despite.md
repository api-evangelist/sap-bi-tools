---
title: "BAPI_SALESORDER_CHANGE Not Updating Cost Center Despite Successful Processing Messages"
url: "https://community.sap.com/t5/abap-forum/bapi-salesorder-change-not-updating-cost-center-despite-successful/m-p/14482408#M1200"
date: "2026-09-09"
author: "ronaldo_aparecido"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
I am using the BAPI_SALESORDER_CHANGE to update the Cost Center of a sales order from a blank value to a valid one. The BAPI execution returns the following messages, which do not appear to be errors, only informational/warning messages. However, the Cost Center is not being updated: "ORDER_HEADER_IN processed successfully" "Sales and distribution document is still incomplete -> please complete it" "Donation M1 Face 444840163 has been saved." When I check the document in VA03 to understand why it is considered incomplete, SAP indicates that the reason is the Cost Center field itself.
