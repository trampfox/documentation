---
title: Docker
kind: documentation
disable_toc: false
---

## Overview

TKTK

**[INSTRUCTIONS ARE WIP]**

## Install the Observability Pipelines Worker

1. On the onboarding page, select **Docker** in the **Choose your installation platform** dropdown menu.
1. The environment variables you need to provide depends on the source you selected.
{{< tabs >}}
{{% tab "Splunk HEC" %}}

a. Enter the Splunk HEC token in the **Splunk_Token** field.   
b. Enter the Splunk HEC endpoint URL. For example `https://<your_account>.splunkcloud.com:8088/services/collector/event`. See [Send Data to HTTP Event Collector][1] for more information.

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
1. Click **Select an API key** to choose the Datadog API key you want to use to send your logs to Datadog.
1. Run the command provided to install the Worker.
1. Run the following command to start the worker:

```
sudo systemctl restart observability-pipelines-worker
```

After the workers are installed, navigate back to the onboarding page and click **Deploy** to deploy your pipeline.