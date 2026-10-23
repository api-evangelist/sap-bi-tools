---
title: "What are the ADT handler class names for each ADT URI prefix?"
url: "https://community.sap.com/t5/abap-forum/what-are-the-adt-handler-class-names-for-each-adt-uri-prefix/m-p/14505579#M1367"
date: "2026-10-16"
author: "Sandra_Rossi"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
In ADT, after pressing Ctrl+Shift+A (open object dialog) and typing RSAQEXCE, I can see this entry in the ABAP Communication Log: GET /sap/bc/adt/repository/informationsystem/search?operation=quickSearch&query=RSAQEXCE*&maxResults=51 HTTP/1.1 (*) The ABAP class response is: http://www.sap.com/adt/core "> I want to know why the ABAP class returns adtcore:type="PROG/I" (I'd like it to return FUGR/F). How can I find out quickly the ADT handler class name in order to debug the logic immediately? Is there a table of ADT handler class names for each ADT URI prefix?
