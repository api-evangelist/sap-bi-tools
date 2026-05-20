---
title: "OData Deep Insert: Implementation and Real-Life Examples"
url: "https://community.sap.com/t5/application-development-and-automation-blog-posts/odata-deep-insert-implementation-and-real-life-examples/ba-p/14147054"
date: "Mon, 15 Sep 2025 06:37:09 GMT"
author: "SRSATAPATHY"
feed_url: "https://community.sap.com/khhcw49343/rss/board?board.id=application-developmentblog-board"
---
OData Deep Insert is used when we need to create a main record along with its related records in one go. For example, if we're creating a sales order and want to include multiple items in that order, instead of calling the service multiple times (once for the header and once for each item), we can just send everything together in one request. This helps reduce the number of API calls and keeps things more efficient.
