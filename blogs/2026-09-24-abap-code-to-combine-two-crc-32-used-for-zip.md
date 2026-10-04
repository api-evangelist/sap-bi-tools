---
title: "ABAP code to combine two CRC-32 used for ZIP"
url: "https://community.sap.com/t5/abap-forum/abap-code-to-combine-two-crc-32-used-for-zip/m-p/14491318#M1257"
date: "2026-09-24"
author: "Sandra_Rossi"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
I need code which combines two CRC-32 like the onces produced by CL_ABAP_ZIP=>CRC32 (algorithm "HDLC" AKA "IEEE 802.3", LSB-Least Significant Byte first which corresponds to the polynomial EDB88320 ), like Zlib's crc32_combine function . For information, I want it to generate a very large ZIP file (CL_ABAP_ZIP can't do that because it can zip only in one go with an XSTRING parameter which is limited to approximately 2GB). As CL_ABAP_ZIP is based on GZIP, the class CL_ABAP_GZIP_BINARY_STREAM could be used instead to zip the huge data by sections of 2GB or less, but the calculation of the CRC ha
