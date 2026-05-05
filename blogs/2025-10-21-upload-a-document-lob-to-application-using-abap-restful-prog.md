---
title: "Upload a Document (LOB) to Application using ABAP Restful programming."
url: "https://community.sap.com/t5/application-development-and-automation-blog-posts/upload-a-document-lob-to-application-using-abap-restful-programming/ba-p/14227768"
date: "Tue, 21 Oct 2025 12:01:54 GMT"
author: "Swasthik3012"
feed_url: "https://community.sap.com/khhcw49343/rss/board?board.id=application-developmentblog-board"
---
<h2><strong>Introduction</strong></h2><p>Uploading large files like Excel sheets or images is a frequent requirement in many business applications. Previously, in RAP-based applications, the only way to handle such uploads was by extending the application and using UI5 tooling to support file uploads manually.</p><p>However, with the release of SAP BTP ABAP environment version 2208, the RAP framework has introduced support for <strong>OData streams</strong>. This enhancement now allows developers to natively manage and process <strong>Large Objects (LOBs)</strong> directly within RAP applications. It enables end users to upload various external file types — including PDFs, XLSX files, binary formats, and other media — without custom extensions or additional tooling.</p><p>In this blog, we’ll walk through how to implement file upload functionality for large objects (like PDFs or binary files) within a standard RAP application, making full use of the new stream handling capabilities — and all without extending the UI manually.</p>
