---
title: "BAPI_GOODSMVT_CREATE returns KE0C 134 (STEUC)"
url: "https://community.sap.com/t5/abap-forum/bapi-goodsmvt-create-returns-ke0c-134-steuc/m-p/14482721#M1202"
date: "2026-09-10"
author: "Charan-p_30"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
Hi Experts, We are facing a strange issue with BAPI_GOODSMVT_CREATE in our SAP system. We have a custom ABAP program that calls: CALL FUNCTION 'BAPI_GOODSMVT_CREATE' EXPORTING goodsmvt_header = lw_hdr goodsmvt_code = lw_code testrun = lw_test IMPORTING goodsmvt_headret = lw_hdr_ret materialdocument = lv_materialdocument matdocumentyear = lv_matdocumentyear TABLES goodsmvt_item = lt_item return = lt_return. Issue The BAPI call itself has SY-SUBRC = 0 , but RETURN contains an error: TYPE = E ID = KE0C NUMBER = 134 MESSAGE_V1 = STEUC The message starts with: "The dependent characteristic STEUC (C
