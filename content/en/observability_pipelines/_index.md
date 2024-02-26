---
title: Observability Pipelines
kind: documentation
disable_toc: false
further_reading:
  - link: /observability_pipelines/set_up_pipelines/
    tag: Documentation
    text: Set up Observability Pipelines
---

## Overview

Observability Pipelines allows you to collect, process, and route logs based on the following use cases:

- [Log volume control](#log-volume-control)
- [Dual ship logs](#dual-ship-logs)
- [Split logs](#split-logs)
- [Archive logs](#archive-logs)
- [Redact data before routing your logs to a destination](#redact-data)

The Observability Pipelines Worker is the software that runs in your infrastructure. It aggregates and centrally processes and routes your data based on the selected use case.

The Datadog UI provides a control plane to manage your Observability Pipelines Workers. You can monitor your pipelines to understand the health of your pipelines, identify bottlenecks and latencies, and investigate your largest volume contributors.

These are the available sources for each use case:

| Use case           | Splunk HEC | Splunk TCP | Sumo Logic | Datadog Agent|
| -----------------  | :--------: | :--------: | :--------: | :-----------:|
| Dual ship logs     |  {{< X >}} |  {{< X >}} | {{< X >}}  |              |
| Log volume control |  {{< X >}} |  {{< X >}} | {{< X >}}  |              |
| Split logs         |  {{< X >}} |  {{< X >}} | {{< X >}}  |  {{< X >}}   |
| Archive logs       | {{< X >}}  |  {{< X >}} | {{< X >}}  |  {{< X >}}   |
| Redact data        |  {{< X >}} |  {{< X >}} | {{< X >}}  |  {{< X >}}   |

### Log volume control

As your organization scales, your log volume grows and the cost of ingesting and indexing in your downstream services (for example, log management solutions, SIEMs, and so forth) also rises. Use Observability Pipelines to cut down on your log volume and trim down the size of your logs before data leaves your infrastructure or network.

### Dual ship logs

Use Observability Pipelines to dual ship your logs to Datadog and another destination.

### Split logs

Use Observability Pipelines to send your devops logs to Datadog and security logs to another destination.

### Archive logs

Use Observability Pipelines to format logs into a Datadog-rehydratable format and then route them directly to Log Archives. These logs are not ingested into Datadog, but are routed directly to the archive. You can then rehydrate the archive in Datadog when you need to analyze and investigate them.

The Observability Pipelines Datadog Archives destination is useful when:

- You have a high volume of noisy logs, but you may need to index them in Log Management ad hoc.
- You have a retention policy.

### Redact data

Sensitive data, such as credit card numbers, bank routing numbers, and API keys, can be revealed unintentionally in your logs, which can expose your organization to financial and privacy risks. Use the Observability Pipelines to identify, tag, and optionally redact or hash sensitive information before routing the data to its destination. You can use out-of-the-box scanning rules to detect common patterns such as email addresses, credit card numbers, API keys, authorization tokens, and more. Or, create custom scanning rules using regex patterns to match sensitive information.

## Get started

1. [Configure your log source][1].
1. [Set up a pipeline based on a use case][2].
1. [Install the Observability Pipelines Worker][3].
1. [Connect your log source to the Worker][4].
1. [Enable monitors][LINK] to get alerted on issues such as CPU and memory utilization.

## Further reading

{{< partial name="whats-next/whats-next.html" >}}

[1]: /observability_pipelines/set_up_pipelines?tab=splunkhec#configure-your-log-source
[2]: /observability_pipelines/set_up_pipelines/?tab=splunkhec#set-up-a-pipeline
[3]: /observability_pipelines/set_up_pipelines?tab=splunkhec#install-the-observability-pipelines-worker
[4]: /observability_pipelines/set_up_pipelines?tab=splunkhec#connect-your-log-source-to-the-observability-pipelines-worker


