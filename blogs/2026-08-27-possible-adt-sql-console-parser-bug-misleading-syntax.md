---
title: "Possible ADT SQL Console parser bug: misleading syntax errors for valid Open SQL statement"
url: "https://community.sap.com/t5/abap-forum/possible-adt-sql-console-parser-bug-misleading-syntax-errors-for-valid-open/m-p/14474041#M1170"
date: "2026-08-27"
author: "nemanjasimovicavnet"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
Hi everyone, I believe I may have found a bug or limitation in the ADT SQL Console and would like to know whether anyone else has experienced similar behavior. System: SAP ECC (Oracle database, not HANA) ADT SQL Console in Eclipse Not working SQL ⛔ I have below Open SQL query which is 320 characters long (it matters 😉 😞 select ltap~tanum, count(*) as count from ltap as ltap where ltap~lgnum = 'STN' and exists ( select 1 from ltap as l1 where l1~lgnum = 'STN' and l1~tanum = ltap~tanum and l1~werks = 'DER6' ) group by ltap~tanum having min( ltap~werks ) <> max( ltap~werks ) Here is a screenshot:
