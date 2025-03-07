---

copyright:
  years:  2018, 2021
lastupdated: "2021-03-28"

keywords: IBM Cloud, monitoring, monitoring agent, event filters

subcollection: monitoring

---

{{site.data.keyword.attribute-definition-list}}


# Filtering events by severity
{: #agent_events_level}

When you delete an {{site.data.keyword.mon_full_notm}} instance, or if you want to stop collecting metrics from a source, you must uninstall the monitoring agent from sources where it was installed as a service. If you deployed a monitoring agent as a container, you must run docker commands to remove the agent.
{: shortdesc}




## Filtering events by severity
{: #severity}

To filter events by severity, you can also change the log entry type for events in the *dragent.yaml* file. 

The default log level is **information**. This means that only warning and higher severity events are transmitted.

Valid levels are: *emergency*, *alert*, *critical*, *error*, *warning*, *notice*, *information*, *debug* and *none*. **Note**: The values are listed from high priority to low priority.

For example, to filter out low severity events (*notice*, *information*, *debug*), you must set the log section **event_priority** to *warning*:

```text
log:
  event_priority: warning
```
{: codeblock}


To block collection of events, you must set the log section **event_priority** to *none*:

```text
log:
  event_priority: none
```
{: codeblock}




### Filtering Kubernetes events by severity
{: #change_kube_agent_event_filterby_severity}

* The **event_priority** in the **log** section controls the type of events that are sent from the agent
* The default log level is *information*. This means that only information and higher severity events are transmitted.
* Valid levels are: *emergency*, *alert*, *critical*, *error*, *warning*, *notice*, *information*, *debug* and *none*. **Note**: The values are listed from high priority to low priority.
* Setting the level to `none` will block all event collection.

