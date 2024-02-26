---
title: Set Up Pipelines
kind: documentation
disable_toc: false
---

## Overview

The following use cases are available for you to start using Observability Pipelines:

- Log volume control: Cut down on your log volume and trim down the size of your logs before data leaves your infrastructure or network.
- Dual ship logs: Send your logs to Datadog and another destination.
- Split logs: Send your devops logs to Datadog and security logs to another destination.
- Archive logs: Send logs to Datadog log archives and another destination.
- Redact data before routing your logs to a destination.

These are the available sources for each use case:

| Use case           | Splunk HEC | Splunk TCP | Sumo Logic | Datadog Agent|
| -----------------  | :--------: | :--------: | :--------: | :-----------:|
| Dual ship logs     |  {{< X >}} |  {{< X >}} | {{< X >}}  |              |
| Log volume control |  {{< X >}} |  {{< X >}} | {{< X >}}  |              |
| Split logs         |  {{< X >}} |  {{< X >}} | {{< X >}}  |  {{< X >}}   |
| Archive logs       | {{< X >}}  |  {{< X >}} | {{< X >}}  |  {{< X >}}   |
| Redact data        |  {{< X >}} |  {{< X >}} | {{< X >}}  |  {{< X >}}   |

This document walks you through the following steps for setting up Observability Pipelines:

1. [Configure your log source](#configure-your-log-source).
1. [Set up a pipeline](#set-up-a-pipeline).   
    a. Select your log source.   
    b. Add processors to manipulate your log data.   
    c. Configure the destinations to send your logs to.  
    d. Install the Observability Pipelines Worker.
1. [Connect your log source to the Observability Pipelines Worker](#connect-your-log-source-to-the-observability-pipelines-worker).

## Configure your log source

Follow the instructions to configure your log source.

**[INSTRUCTIONS ARE WIP]**

{{< tabs >}}
{{% tab "Splunk HEC" %}}

### Set up the Splunk index

<div class="alert alert-info">Observability Pipelines supports acknowledgments when you enable the <strong>Enable Indexer Acknowledgments</strong> setting on the input. Indexer acknowledgement is only available for Splunk Enterprise</div>

You must provision a Splunk HEC input and HEC token on the Splunk index so that the Observability Pipelines Worker can send logs to Splunk. Follow the instructions in the [Configure HTTP Event Collector on Splunk Cloud Platform][1] section.

After configuring the HTTP Event Collector, use the Splunk HEC token to set up Observability Pipelines.

[1]: https://docs.splunk.com/Documentation/Splunk/latest/Data/UsetheHTTPEventCollector

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


## Set up a pipeline

1. Navigate to [Observability Pipelines][LINK].
1. Select a use case.
1. Select a log source.

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

1. Enter the Splunk Index.
1. Select if you want the logs encoded in **JSON** or **Raw**.
1. Select **Auto Extract Timestamp** if you to enable it.
1. Enter the sourcetype.
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

**[INSTRUCTIONS ARE WIP]**

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

After the workers are installed, navigate back to the onboarding page and click **Deploy** to deploy your pipeline.

## Connect your log source to the Observability Pipelines Worker

Follow the instructions to connect your specific log source to the Worker.

**[INSTRUCTIONS ARE WIP]**

{{< tabs >}}
{{% tab "Splunk HEC" %}}

### Set up the Splunk index

Update your Splunk collector with the HEC token that you created earlier and used for setting up the Observability Pipelines Worker.

You can update most HEC-compatible collectors with the IP/URL of the host (or load balancer) associated with the Observability Pipelines Worker to send your logs to the Worker. For Terraform installs, the `lb-dns` output provides the value to use. For CloudFormation installs, the `LoadBalancerDNS` CloudFormation output provides the URL to use.

{{% /tab %}}
{{% tab "Splunk TCP" %}}

### Connect your Splunk connector to the Worker


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

After your log source is connected to the Worker, you can see the throughput of logs flowing through the pipeline in the [Pipelines][LINK] page. If you want to see the actual logs, go to the destination the logs are sent to. For example, if logs are sent to Datadog, go to the [Log Explorer][2] to see your logs.

[2]: https://app.datadoghq.com/logs