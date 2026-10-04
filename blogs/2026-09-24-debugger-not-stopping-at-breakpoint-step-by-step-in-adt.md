---
title: "Debugger not stopping at breakpoint, step by step in ADT always shows line 1, unknown code position"
url: "https://community.sap.com/t5/abap-forum/debugger-not-stopping-at-breakpoint-step-by-step-in-adt-always-shows-line-1/m-p/14490967#M1255"
date: "2026-09-24"
author: "Sandra_Rossi"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
In ADT, I added a breakpoint in the first line of method IF_SALV_GUI_LEX_FMTR_BEHAVIOR~FORMAT of class CL_SALV_GUI_LEX_FMTR_CHECKBOX, ran the code (an ALV export), I am sure that the method was called, but ADT didn't stop at the breakpoint. If I add a breakpoint just before the call (one line in the method IF_SALV_GUI_LEX_FORMATTER~FORMAT_VALUE_CELL of CL_SALV_GUI_LEX_FORMATTER) and I click F5 (step by step), the debugger shows the source code of CL_SALV_GUI_LEX_FMTR_CHECKBOX, with the cursor at the line 1 of the class (not the method), and F5 again shows again the cursor at the line 1. In fac
