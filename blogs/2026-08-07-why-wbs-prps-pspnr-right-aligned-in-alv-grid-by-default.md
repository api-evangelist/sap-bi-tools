---
title: "Why WBS PRPS-PSPNR right-aligned in ALV Grid by default? (field of type NUMC but conv exit to text)"
url: "https://community.sap.com/t5/abap-forum/why-wbs-prps-pspnr-right-aligned-in-alv-grid-by-default-field-of-type-numc/m-p/14459560#M1161"
date: "2026-08-07"
author: "Sandra_Rossi"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
Why is PRPS-PSPNR right-aligned by default in ALV Grid? (simple demo program below) I understand that PRPS-PSPNR is of type NUMC (number as text, which cannot be summed for instance, like a ZIP code), but it has a conversion exit which transforms it to text. Code: REPORT zdemo.
