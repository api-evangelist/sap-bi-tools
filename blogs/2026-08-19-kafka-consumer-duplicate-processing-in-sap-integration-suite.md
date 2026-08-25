---
title: "Kafka Consumer Duplicate Processing in SAP Integration Suite"
url: "https://community.sap.com/t5/integration-forum/kafka-consumer-duplicate-processing-in-sap-integration-suite/m-p/14467767#M347"
date: "2026-08-19"
author: "Marielo"
feed_url: "https://community.sap.com/khhcw49343/rss/Community?interaction.style=forum"
---
Hi everyone, I'm investigating a Kafka consumer behavior in SAP Integration Suite where the same message is sporadically processed by different BTP runtime instances. I was able to reproduce the behavior in our DEV tenant using a simple iFlow. Configuration / Default: Kafka Partitions: 1 Parallel Consumers: 1 Error Handling: Skip Failed Message Heartbeat Interval: 3 seconds Session Timeout: 10 seconds Request Timeout: 30 seconds Why did I add a 2-minute delay?
