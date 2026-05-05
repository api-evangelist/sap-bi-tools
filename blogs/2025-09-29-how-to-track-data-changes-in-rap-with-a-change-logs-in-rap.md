---
title: "How to Track Data Changes in RAP with a  Change Logs in RAP."
url: "https://community.sap.com/t5/application-development-and-automation-blog-posts/how-to-track-data-changes-in-rap-with-a-change-logs-in-rap/ba-p/14218316"
date: "Mon, 29 Sep 2025 07:04:02 GMT"
author: "Gireesh_pg1"
feed_url: "https://community.sap.com/khhcw49343/rss/board?board.id=application-developmentblog-board"
---
<div class=""><div class=""><div class=""><div class=""><div class=""><div class=""><p>In the RAP model, a <strong>change log table</strong> provides an efficient way to track modifications without maintaining full historical data snapshots. Instead of duplicating entire records, the main table continues to store only the current business data, while the change log table captures key details about each modification, such as record identifiers, type of change (insert, update, delete), user information, and optional reasons for the update. These entries are written during the RAP save sequence through determinations in the behavior implementation. This lightweight mechanism creates a reliable audit trail that helps with compliance checks, reporting, and troubleshooting, while significantly reducing storage overhead compared to a shadow table that preserves complete data history.</p></div></div></div></div><div class="">&nbsp;</div><div class=""><div class="">&nbsp;</div></div></div></div><div class="">&nbsp;</div>
