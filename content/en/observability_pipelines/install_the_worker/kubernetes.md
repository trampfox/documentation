---
title: Kubernetes
kind: documentation
disable_toc: false
---

## Overview

TKTK

**[INSTRUCTIONS ARE WIP]**

## Install the Observability Pipelines Worker

1. On the onboarding page, select **Kubernetes** in the **Choose your installation platform** dropdown menu.
1. Select your cloud provider.

### Provide your environment variables 
1. The information variables you need to provide depends on your source.

{{< tabs >}}
{{% tab "Splunk HEC" %}}

1. Enter the Splunk HEC token in the **Splunk_Token** field.
1. 1. Enter the Splunk HEC endpoint URL. For example `https://<your_account>.splunkcloud.com:8088/services/collector/event`. See [Send Data to HTTP Event Collector][1] for more information.

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

### Download and run the Helm chart

Download the Helm chart values file for your cloud provider.

{{< tabs >}}
{{% tab "AWS EKS" %}}

1. Download the [Helm chart values file][link] for AWS EKS.
1. In the Helm chart values file, replace `site` with {{< region-param key="dd_site" code="true" >}}. Make sure you have the correct site region selected in the upper right side of the page to show the site URL you need to use. See [Datadog Site][2] for more information.
1. Click **Select an API key** to choose the Datadog API key you want to use to send your logs to Datadog.
1. Run the command provided to install the worker in your environment.

[2]: /getting_started/site/

{{% /tab %}}
{{% tab "Azure AKS" %}}

TKTK

{{% /tab %}}
{{% tab "Google GKE" %}}

TKTK

{{% /tab %}}
{{< /tabs >}}

After the workers are installed, navigate back to the onboarding page and click **Deploy** to deploy your pipeline.