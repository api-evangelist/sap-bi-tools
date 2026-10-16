---
title: "Consult about BAPI_SALESORDER_CHANGE to update REASON_REJ"
url: "https://community.sap.com/t5/abap-forum/consult-about-bapi-salesorder-change-to-update-reason-rej/m-p/14497814#M1324"
date: "2026-10-06"
author: "tracyhang"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
I tried to use BAPI_SALESORDER_CHANGE to update REASON_REJ, but the system error disappeared as bellows: TYPE=E ID=KK NUMBER=049 MSG=Enter costing sheet V1= V2= V3= V4= TYPE=E ID=V4 NUMBER=248 MSG=Error in ITEM_IN 002000 V1=VBAPKOM V2=002000 V3= V4= TYPE=E ID=V4 NUMBER=219 MSG=Sales document *** was not changed V1=*** V2=002000 V3= V4= Please kindly guide how to solve it. Many thanks! The code is: public static int ChangeSalesOrder(RfcDestination prd, string salesOrder, out string msg) { msg = ""; try { RfcRepository SapRfcRepository = prd.Repository; IRfcFunction function = SapRfcRepository.C
