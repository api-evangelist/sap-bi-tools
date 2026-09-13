---
title: "SM30 maintenance view on tables ZZZB ZZZA, where clause on ZZZA field doesn't filter out ZZZB lines"
url: "https://community.sap.com/t5/abap-forum/sm30-maintenance-view-on-tables-zzzb-zzza-where-clause-on-zzza-field-doesn/m-p/14481511#M1193"
date: "2026-09-08"
author: "Sandra_Rossi"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
I've got two tables ZZZA and ZZZB. ZZZA has just 3 columns CLIENT, OBJTYPE, OBJKEY, nothing else special. ZZZB has columns CLIENT and OBJKEY with a foreign key to ZZZA as follows: I have created this maintenance view ZZZV (NB: I have defined the tables ZZZB and ZZZA in this order, via the button "Relationships", ZZZA appearing in the section "Referenced tables", because it wasn't possible to define ZZZA then ZZZB, because ZZZB was listed in the section "Relationships with unsuitable cardinality", I'm not sure if the order of tables is important or not): Note that the foreign key constant selec
