---
title: "CAP CDS Compiler Error: Naming conflict / limitation when flattening association with matching targe"
url: "https://community.sap.com/t5/sap-cap-forum/cap-cds-compiler-error-naming-conflict-limitation-when-flattening/m-p/14457317#M96"
date: "2026-08-06"
author: "Nirmal_selvaraja-015"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
Hi SAP Community, I am building a CAP application and encountered a behavior with the CDS compiler regarding inline projection/flattening of associations that feels like a compiler limitation or edge-case bug. I have two entities in my schema (PurchaseOrders and GoodsReceipts). When trying to project their associations in a service definition using the simple as NewName shortcut, one works flawlessly while the other fails with a compilation error.
