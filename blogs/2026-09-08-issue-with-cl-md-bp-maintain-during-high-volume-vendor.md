---
title: "Issue with CL_MD_BP_MAINTAIN During High-Volume Vendor Company Code Expansion"
url: "https://community.sap.com/t5/abap-forum/issue-with-cl-md-bp-maintain-during-high-volume-vendor-company-code/m-p/14481865#M1197"
date: "2026-09-08"
author: "ronaldo_aparecido"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
I am using the CL_MD_BP_MAINTAIN=>MAINTAIN method to perform a mass expansion of millions of vendors, with the entire process being executed inside a loop. For example, vendors that already exist in company code 001 need to be expanded to company code 881. The issue is that, in some cases, the method indicates that the expansion was completed successfully, but when I later verify the data in the system, I find that certain vendors were not actually expanded.
