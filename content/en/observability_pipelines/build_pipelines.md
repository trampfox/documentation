---
title: Build Pipelines
kind: documentation
disable_toc: false
---

## Overview

The following use cases are available for you to start creating your pipelines in Observability Pipelines:

- Log volume control: Cut down on your log volume and trim down the size of your logs before data leaves your infrastructure or network.
- Dual ship logs: Send your logs to Datadog and another destination.
- Split logs: Send your devops logs to Datadog and your security logs to another destination.
- Archive logs: Send logs to Datadog log archives and another destination.
- Redact data before routing your logs to a destination.

After you select one of the use cases, [create your pipeline](#create-a-pipeline) with the following steps:

1. Select a log source.
1. Add processors to manipulate your log data.
1. Configure the destinations to send your logs to.

**[INSTRUCTIONS ARE WIP]**

## Create a pipeline

1. Navigate to [Observability Pipelines][LINK].
1. Select a use case.

### Select a log source

These are the available sources for each use case:

| Use case           | Splunk HEC | Splunk TCP | Sumo Logic | Datadog Agent|
| -----------------  | ---------- | ---------- | ---------- | -------------|
| Dual ship logs     |  {{< X >}} |  {{< X >}} | {{< X >}}  |              |
| Log volume control |  {{< X >}} |  {{< X >}} | {{< X >}}  |              |
| Split logs         |  {{< X >}} |  {{< X >}} | {{< X >}}  |  {{< X >}}   |
| Archive logs       | {{< X >}}  |  {{< X >}} | {{< X >}}  |  {{< X >}}   |
| Redact data        |  {{< X >}} |  {{< X >}} | {{< X >}}  |  {{< X >}}   |

After you select a source on the onboarding page, you need to provide the following information:

{{< tabs >}}
{{% tab "Splunk HEC" %}}

1. Select **Splunk HEC** as the source.
1. Enter the Splunk HEC endpoint in the Splunk HEC **Address** field. For example `https://<your_account>.splunkcloud.com:8088/services/collector/event`. See [Send Data to HTTP Event Collector][1] for more information.
1. Optionally, enter the Splunk HEC token.

[1]: https://docs.splunk.com/Documentation/Splunk/latest/Data/UsetheHTTPEventCollector#Send_data_to_HTTP_Event_Collector

{{% /tab %}}
{{% tab "Splunk TCP" %}}

Text inside tab. [Link references][1] must be inside the tab.

[1]: /agent/guide/agent-commands/

{{% /tab %}}

{{% tab "Sumo Logic" %}}

Text inside tab. [Link references][1] must be inside the tab.

[1]: /agent/guide/agent-commands/

{{% /tab %}}
{{% tab "Datadog Agent" %}}

Text inside tab. [Link references][1] must be inside the tab.

[1]: /agent/guide/agent-commands/

{{% /tab %}}
{{< /tabs >}}

### Add processors

There are pre-selected processors and you can add additional processors for your use case. The following processors are available:
**[INSTRUCTIONS ARE WIP]**

{{< tabs >}}
{{% tab "Filter" %}}

Add a query to filter your logs.

{{% /tab %}}
{{% tab "Sampler" %}}

1. Add a query to filter your logs
1. Enter the percent of logs to sample.

{{% /tab %}}
{{% tab "Quota" %}}

1. Add a query to filter you logs.
1. Select in the **Enforce by** dropdown menu how do you want to determine the quota.
1. Enter the daily quota limit.

{{% /tab %}}
{{% tab "Remap" %}}

Select one of the following types of reamp in the dropdown menu:

#### Add a field

1. Select the field.
1. Add a query.
1. Enter the key and value you want to add.

#### Drop a field

1. Add a query to filter to logs.
1. Enter the key you want to drop.

#### Rename a field

1. Add a query to filter the logs.
1. Enter the key that you want to remap.
1. Enter the key that you want the original key to be remapped to.
1. If you to do not want to keep the original source tag, uncheck **Preserve source tag**.

{{% /tab %}}
{{< /tabs >}}

### Configure the destinations for your logs

The destinations are automatically selected for you based on the use case and the source you selected.

**[INSTRUCTIONS ARE WIP]**

{{< tabs >}}
{{% tab "Splunk HEC" %}}

1. Enter in the Splunk endpoint URL.

[1]: https://docs.splunk.com/Documentation/Splunk/latest/Data/UsetheHTTPEventCollector#Send_data_to_HTTP_Event_Collector

{{% /tab %}}
{{% tab "Splunk TCP" %}}

Text inside tab. [Link references][1] must be inside the tab.

[1]: /agent/guide/agent-commands/

{{% /tab %}}

{{% tab "Sumo Logic" %}}

Text inside tab. [Link references][1] must be inside the tab.

[1]: /agent/guide/agent-commands/

{{% /tab %}}
{{% tab "Datadog" %}}

Text inside tab. [Link references][1] must be inside the tab.

[1]: /agent/guide/agent-commands/

{{% /tab %}}
{{< /tabs >}}

## Install the Observability Pipelines Worker

Select your platform in the **Choose your installation platform** dropdown menu.

**[INSTRUCTIONS ARE WIP]**

{{< tabs >}}
{{% tab "Docker" %}}

1. Enter the Splunk HEC token ino the **Splunk_Token** field.
1. Enter the Splunk HEC endpoint in the Splunk HEC **Address** field. For example `https://<your_account>.splunkcloud.com:8088/services/collector/event`. See Send Data to HTTP Event Collector for more information.
1. Click **Select an API key** to choose the Datadog API key you want to use.
1. Run the provided command to install the Worker.
1. Run the following command to start the worker:

```
sudo systemctl restart observability-pipelines-worker
```

{{% /tab %}}
{{% tab "AWS EKS" %}}

1. Download the [Helm chart values file][link] for AWS EKS.
1. In the Helm chart values file, replace `site` with {{< region-param key="dd_site" code="true" >}}. Make sure you have the correct site region selected in the upper right side of the page to show the site URL you need to use. See [Datadog Site][2] for more information.
1. To install the Worker, run the following commands:

    ```shell
    helm repo add datadog https://helm.datadoghq.com
    ```

    ```shell
    helm repo update
    ```

    ```shell
    helm upgrade --install \
        opw datadog/observability-pipelines-worker \
        -f aws_eks.yaml
    ```

[2]: /getting_started/site/

{{% /tab %}}
{{% tab "Azure AKS" %}}

TKTK

{{% /tab %}}
{{% tab "Google GKE" %}}

TKTK

{{% /tab %}}
{{% tab "Linux (APT)" %}}

TKTK

{{% /tab %}}
{{% tab "Linux (RPM)" %}}

TKTK

{{% /tab %}}
{{% tab "CloudFormation" %}}

TKTK
{{% /tab %}}
{{% tab "Terraform (AWS)" %}}

TKTK

{{% /tab %}}
{{< /tabs >}}