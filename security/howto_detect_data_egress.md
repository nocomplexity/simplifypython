# How to Check for Data Exfiltration

**[Python Code Audit](https://nocomplexity.com/codeaudit/)** includes functionality to detect potential data exfiltration risks. This feature is available through:

- the [CLI interface](userguide), and

- the [API](apidocs/modules).

Using the CLI

The egress detection function can be activated with the following command:
```bash
codeaudit filescan <pythonfile|package-name|directory> [OUTPUTFILE]
```

**Report Output**

In the generated HTML report, each analysed file is evaluated for potential data exfiltration to external services.

If a potential risk is detected, the report will display:
> *&#9888;&#65039; External Egress Risk: Detected outbound connection logic or API keys that may facilitate data egress.*

The report also highlights the exact lines of code that triggered the detection.

If no external egress risks are identified, the report will display:
> *&#x2705; No logic for connecting to remote services found. Risk of data exfiltration to external systems is low.*

:::{important} 
No tool can provide 100% guarantees. This applies to Python Code Audit as well as to any other security analysis tool.
:::

Data egress exposes Python applications to a wide range of security threats and risks:


| Category                 | Threat / Risk             | Examples                         | Risk Level |
|--------------------------|---------------------------|---------------------------------|------------|
| Telemetry & Observability| Data Leakage / Privacy    | Datadog, New Relic, AppDynamics | 🔴 High   |
| Logging & Analytics      | Metadata Exposure         | Splunk, ELK, Loggly             | 🟠 Medium |
| Cloud Infrastructure     | Lateral Movement          | AWS, Azure, GCP                  | 🔴 High   |
| AI & LLM Pipelines       | Resource Abuse / IP Leak  | OpenAI, Anthropic, LangChain    | 🟠 Medium |
| Communication Gateways   | Financial Risk / Phishing | Twilio, SendGrid, Slack Webhooks| 🔴 High   |


:::{admonition} High-risk integrations are a key focus for [Python Code Audit](https://nocomplexity.com/codeaudit/) egress detection!
:class: danger, dropdown

The following categories represent common classes of external service integrations that may introduce data egress or external communication risks in Python applications.

| Category | Risk Type | Typical Detection Indicators | Examples |
|----------|-----------|-----------------------------|----------|
| Telemetry & Observability | Data Leakage / Privacy | Telemetry SDK imports, metrics exporters, remote monitoring endpoints, automatic usage reporting | Datadog, New Relic, AppDynamics, Mixpanel, Segment |
| Logging & Analytics | Metadata Exposure | Remote log ingestion endpoints, log shipping agents, API tokens for log platforms | Splunk, ELK (Elastic), Loggly |
| Cloud Infrastructure | Lateral Movement | Cloud SDK usage, IAM credential usage, storage APIs, service account authentication | AWS (IAM/S3), Azure (Service Principals), GCP |
| AI & LLM Pipelines | Resource Abuse / IP Leak | LLM API calls, prompt transmission to external APIs, model inference endpoints | OpenAI, Anthropic, LangChain |
| Communication Gateways | Financial Risk / Phishing | Messaging APIs, webhook endpoints, outbound email/SMS integrations | Twilio, SendGrid, Slack Webhooks |

:::

