---
title: "Wrong ABAP documentation for NEW-PAGE Obsolete Specification of Spool Parameters"
url: "https://community.sap.com/t5/abap-forum/wrong-abap-documentation-for-new-page-obsolete-specification-of-spool/m-p/14496177#M1307"
date: "2026-10-02"
author: "Sandra_Rossi"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
Obsolete Specification of Spool Parameters - ABAP Keyword Documentation "flag expects a single-character text field, where a blank character activates the parameter and any other character deactivates the parameter." I think it should be the opposite: "flag expects a single-character text field, where a blank character deactivates the parameter and any other character activates the parameter." For instance, the following means that the spool is sent immediately to the output device: NEW-PAGE PRINT ON DESTINATION 'LOCL' IMMEDIATELY 'X' KEEP IN SPOOL 'X' NO DIALOG. For information, in German it'
