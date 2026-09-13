---
title: "How to create jump report in SAP story dashboard page to another page ?"
url: "https://community.sap.com/t5/data-and-analytics-forum/how-to-create-jump-report-in-sap-story-dashboard-page-to-another-page/m-p/14483285#M190"
date: "2026-09-10"
author: "sumitsamal123"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
Hi All, while user select one field from table_1 on page-1 and click on the navigate button the other page(Page-2) will open with selected dimension as filter . Page-1 then next page same empid filter will apply in page -2 Page-2 These are the sample data button on_click var sel = Table_1.getSelections()[0]; //var dim = Table_1.getDimensionsOnRows()[0]; var selM = sel[Alias.MeasureDimension]; var result = Table_1.getDataSource().getResultMember("EmpID",sel).id; Text_3.applyText(result); Application.setActivePage(Page_2); unable to apply the selected result as filter in page-2.
