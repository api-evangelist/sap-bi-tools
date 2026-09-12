---
title: "S/4HANA Flexible Workflow: How to print Workflow Details on the very first PO PDF output?"
url: "https://community.sap.com/t5/abap-forum/s-4hana-flexible-workflow-how-to-print-workflow-details-on-the-very-first/m-p/14478092#M1177"
date: "2026-09-02"
author: "aleksi46"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
Hi everyone, We are facing an issue trying to get the Approver's Name and Approval Date to print on the very first automated PDF output right after a Purchase Order is approved via the Fiori My Inbox app. We understand that since it's the first print following approval, data won't be available in Workflow tables (i.e. I_WorkflowStatusOverview) yet, so using BAdI MM_PUR_S4_PO_MODIFY_HEADER would not take effect unless PO is changed.
