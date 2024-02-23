---
title: Set Up Pipelines
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

After you select one of the use cases, [set up your pipeline](#set-up-a-pipeline) with the following steps:

1. Select a log source.
1. Add processors to manipulate your log data.
1. Configure the destinations to send your logs to.
1. Install the Observability Pipelines Worker.

**[INSTRUCTIONS ARE WIP]**

## Set up a pipeline

1. Navigate to [Observability Pipelines][LINK].
1. Select a use case.

### Select a log source

These are the available sources for each use case:

| Use case           | Splunk HEC | Splunk TCP | Sumo Logic | Datadog Agent|
| -----------------  | :--------: | :--------: | :--------: | :-----------:|
| Dual ship logs     |  {{< X >}} |  {{< X >}} | {{< X >}}  |              |
| Log volume control |  {{< X >}} |  {{< X >}} | {{< X >}}  |              |
| Split logs         |  {{< X >}} |  {{< X >}} | {{< X >}}  |  {{< X >}}   |
| Archive logs       | {{< X >}}  |  {{< X >}} | {{< X >}}  |  {{< X >}}   |
| Redact data        |  {{< X >}} |  {{< X >}} | {{< X >}}  |  {{< X >}}   |

After you select a source on the onboarding page, you need to provide the following information for the specific source:

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

**[INSTRUCTIONS ARE WIP]**

There are pre-selected processors and you can add additional processors for your use case. The following processors are available:

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
1. Click **Next: Install**.

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

1. Click the tile for your installation platform.
1. The environment variables required depends on the destination.

{{< tabs >}}
{{% tab "Splunk HEC" %}}

3. Enter the Splunk HEC token in the **Splunk_Token** field.
4. Enter the Splunk HEC endpoint URL. For example `https://<your_account>.splunkcloud.com:8088/services/collector/event`. See [Send Data to HTTP Event Collector][1] for more information.

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

Follow the instructions for your platform to install and run the Worker.

{{< tabs >}}
{{% tab "Docker" %}}

1. Click **Select an API key** to choose the Datadog API key you want to use to send your logs to Datadog.
1. Run the command provided to install the Worker.
1. Run the following command to start the worker:
    ```
    sudo systemctl restart observability-pipelines-worker
    ```

[1]: https://hub.docker.com/r/datadog/observability-pipelines-worker
[2]: /resources/yaml/observability_pipelines/datadog/pipeline.yaml

{{% /tab %}}
{{% tab "AWS EKS" %}}

1. Download the [Helm chart values file][link] for AWS EKS.
1. In the Helm chart values file, replace `site` with {{< region-param key="dd_site" code="true" >}}. Make sure you have the correct site region selected in the upper right side of the page to show the site URL you need to use. See [Datadog Site][2] for more information.
1. Click **Select an API key** to choose the Datadog API key you want to use to send your logs to Datadog.
1. Run the command provided to install the worker in your environment.

[2]: /getting_started/site/

{{% /tab %}}
{{% tab "Azure AKS" %}}

1. Download the [Helm chart values file][1] for Azure AKS.

[1]: /resources/yaml/observability_pipelines/datadog/azure_aks.yaml

{{% /tab %}}
{{% tab "Google GKE" %}}

1. Download the [Helm chart values file][1] for Google GKE.

[1]: /resources/yaml/observability_pipelines/datadog/google_gke.yaml

{{% /tab %}}
{{% tab "APT-based Linux" %}}

TKTK

{{% /tab %}}
{{% tab "RPM-based Linux" %}}

TKTK

{{% /tab %}}
{{% tab "Terraform (AWS)" %}}

TKTK

[1]: /resources/yaml/observability_pipelines/datadog/terraform_opw_datadog.tf

{{% /tab %}}
{{% tab "CloudFormation" %}}

TKTK

{{% /tab %}}
{{< /tabs >}}