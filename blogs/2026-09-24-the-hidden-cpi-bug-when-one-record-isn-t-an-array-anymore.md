---
title: "The Hidden CPI Bug: When One Record Isn't an Array Anymore"
url: "https://community.sap.com/t5/abap-forum/the-hidden-cpi-bug-when-one-record-isn-t-an-array-anymore/m-p/14491579#M1262"
date: "2026-09-24"
author: "Mohan-Raj-M"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
Why a Single Item Breaks Your JSON Array in SAP CPI (and How to Fix It) The Problem If you've built a GET API on SAP Integration Suite (CPI) that returns arrays in the JSON response, you've probably run into this classic gotcha: When an element occurs multiple times in the XML, the XML to JSON Converter correctly turns it into a JSON array . When that same element occurs only once , the converter turns it into a plain JSON object instead of a single-item array. This is a huge problem for consuming applications (UI5 apps, external systems, mobile apps, etc.) because they typically expect a cons
