# Sandbox environment

Variables observed in a Perplexity Computer sandbox, as of image `computer/2026.09`.
Collected by reading the process environment inside a sandbox; values are omitted.

## Agent proxy

| variable | notes |
| --- | --- |
| `PPLX_AGENT_PROXY_URL` | Base URL of the agent proxy. |
| `PPLX_AGENT_PROXY_TOKEN` | Workspace bearer. This is the credential the preflight endpoint authenticates with — see [preflight.md](preflight.md). |

## Connectors

| variable | notes |
| --- | --- |
| `PPLX_CONNECTOR_BASE_URL` | Connector service entry point. |
| `PPLX_CONNECTOR_TOOL_TARGET_BASE_URL` | Upstream the proxy forwards tool calls to. On current images the proxy requires this value to be echoed back in an `X-Base-Url` header; omitting it returns `400`, and a value not on the session's allow list returns `403`. |
| `PPLX_CONNECTOR_API_KEY` | Not interchangeable with the agent proxy bearer. |
| `PPLX_CONNECTOR_CONTROL_PLANE_BASE_URL` | |
| `PPLX_CONNECTOR_CONTROL_PLANE_TARGET_BASE_URL` | |
| `PPLX_CONNECTOR_CONTROL_PLANE_API_KEY` | |

## SDK

`PPLX_SDK_BASE_URL`, `PPLX_SDK_TARGET_BASE_URL`, `PPLX_SDK_API_KEY`,
`PPLX_SDK_CONTENT_PREVIEW_CHARS`, `PPLX_SDK_SNIPPET_PREVIEW_CHARS`,
`PPLX_SDK_REPLACE_SNIPPET_WITH_SUMMARY`, `PPLX_SDK_METRICS_FILE`,
`PPLX_SDK_SOURCES_FILE`, `PPLX_SDK_LOG_RESOURCE_ATTRIBUTES`, `PPLX_SDK_COUNTRY`,
`PPLX_OUTPUT_DIR`.

## Telemetry

`OTEL_SERVICE_NAME`, `OTEL_EXPORTER_OTLP_LOGS_ENDPOINT`,
`OTEL_EXPORTER_OTLP_LOGS_HEADERS`, `OTEL_EXPORTER_OTLP_METRICS_ENDPOINT`,
`OTEL_EXPORTER_OTLP_METRICS_HEADERS`, `PPLX_CLI_TELEMETRY_BASE_URL`,
`PPLX_CLI_TELEMETRY_TARGET_BASE_URL`, `PPLX_CLI_TELEMETRY_API_KEY`,
`PPLX_CLI_TELEMETRY_AGENT_ID`.

The exporter bearer in `OTEL_EXPORTER_OTLP_LOGS_HEADERS` is scoped to the telemetry origin.
It is not a workspace bearer and the preflight endpoint rejects it with `403`.

## Not present

| variable | notes |
| --- | --- |
| `SANDBOX_IMAGE_TAG` | Unset on `2026.09`. Checks from that image resolve as `computer/unknown` unless the reporter names the image. |
