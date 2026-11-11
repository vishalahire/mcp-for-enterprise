# Why use MCP when APIs already exist?

An agent can use an existing API through a defined function tool, platform connector or SDK-backed tool. This is a valid production pattern. MCP adds a standardized interface for exposing capabilities to compatible clients, often backed by the same APIs.

Use the [system access decision tree](decision-tree.md) for a concrete choice. The recommendations below are project synthesis, not a requirement to migrate every API.

## What changes in the request path?

| API tool | MCP tool |
| --- | --- |
| The runtime presents a tool definition to the agent. Application or connector code validates arguments, obtains credentials, calls a managed API and shapes the result | An MCP client invokes a tool exposed by an MCP server. The server accesses the underlying source, often through a managed API |
| Tool integration is maintained in the runtime, connector or shared library | The MCP contract provides a common discovery and invocation interface across compatible clients |
| API management and agent-runtime controls govern the path | MCP controls govern the agent-facing path, while backend API and business controls still apply |

“Direct API” means no MCP layer. It does not mean bypassing API management, permissions or audit. Neither approach requires giving credentials to the model or allowing it to construct arbitrary destinations.

OpenAI documents both [function calling](https://developers.openai.com/api/docs/guides/function-calling) and [MCP integration](https://developers.openai.com/api/docs/guides/tools-connectors-mcp). Microsoft documents [exposing selected existing REST operations as MCP tools](https://learn.microsoft.com/en-us/azure/api-management/export-rest-mcp-server). These are supported integration patterns rather than evidence that one is universally preferable.

## Comparison

| Dimension | API tools can be preferable when | MCP can be preferable when |
| --- | --- | --- |
| Coverage | Existing endpoints provide exact fields, operations and filters | Curated MCP tools fully cover the business task |
| Platform fit | An approved API connector or function integration already works well | Compatible MCP clients reduce integration effort |
| Reuse | A shared SDK, OpenAPI contract or connector already meets reuse needs | Multiple client integrations would otherwise duplicate tool adapters |
| Identity | API access supports the required delegation and narrow scopes more faithfully | The MCP route preserves equivalent identity and authorization |
| Governance | API and runtime controls already meet enforcement and audit needs | Shared tool exposure, restrictions, registry and revocation materially simplify management |
| Performance | The measured API path has fewer dependencies and meets tighter objectives | Efficient tools reduce total interaction steps while meeting objectives |
| Maintenance | A small stable integration is cheaper to own | One supported server reduces repeated integration maintenance |
| Vendor support | API support and compatibility exceed the MCP offering | A supported vendor MCP service reduces custom code and operational burden |
| Change control | Explicit endpoint mappings provide the required stability | Approved catalog versions can be centrally distributed and governed |

MCP offers standardized discovery, but discovery is not authorization. Clients should expose an approved subset of tools and review unexpected catalog changes. API contracts and SDKs can also support schema generation and reuse.

A vendor-hosted server can reduce infrastructure work while introducing another data and trust boundary. A self-hosted vendor package adds patching, dependency and support responsibilities. Compare the complete deployment, not just the protocol name.

## What MCP does not automatically provide

- Fresher source data, more accurate answers or stronger source consistency.
- Safer authorization, narrower vendor scopes or correct tenant isolation.
- Better tool descriptions, useful business abstractions or smaller results.
- Lower latency, fewer model turns or lower total cost.
- Durable business approval, transaction rollback or idempotency.
- Access to a system that has no supported underlying integration.

A task-oriented operation such as “get travel summary” can be implemented as either an API tool or MCP tool. Composition is a tool-design choice. Anthropic's [tool engineering guidance](https://www.anthropic.com/research/writing-tools-for-agents) emphasizes useful tools, concise responses, clear descriptions and evaluation; a one-to-one export of every endpoint is not automatically a good agent interface.

## Security and governance responsibilities

| Responsibility | Required treatment |
| --- | --- |
| Identity | Distinguish user identity from workload identity and enforce the intended authority |
| Authorization | Enforce tenant, object and field access at the authoritative service |
| Credentials | Keep secrets out of model context; use approved audience- and scope-bound flows |
| Tool exposure | Allowlist capabilities and validate arguments and destinations |
| Data | Minimize returned fields and constrain model, memory, log and artifact destinations |
| Audit | Correlate agent, tool, gateway and source events without unnecessary sensitive payloads |
| Lifecycle | Own contracts, dependency updates, rollback, revocation and incidents |
| Side effects | Classify actual behavior and enforce risk-based approval at execution |

For MCP, additionally assess server trust, tool-definition changes and the downstream authorization boundary. The [MCP security guidance](https://modelcontextprotocol.io/docs/2025-11-25/tutorials/security/security_best_practices) addresses confused-deputy risks, token passthrough and other implementation hazards. Verify the security specification for the deployed protocol version.

An enterprise may require all MCP traffic to traverse its MCP gateway and all API tools to use approved API/runtime controls. If only one route currently supports a mandatory control, record that implementation constraint. Do not claim that governance intrinsically requires MCP.

Detailed ownership and approvals live in [governance](governance.md) and [governed actions](governed-actions.md).

## Measure before choosing

Compare the same task, source permissions, load, freshness and policy controls. Measure end-to-end latency, p95/p99, successful task rate, throughput, availability, source requests, model turns, payload size and total cost. Include operational ownership and maintenance effort.

A remote MCP hop may add latency and a dependency. A composite tool may reduce round trips. Both API and MCP implementations can use composition, caching and batching. MCP itself does not require another model invocation.

## Practical adoption rule

Keep a qualified API tool when it meets the need economically. Reuse qualified MCP when it provides demonstrated integration or management value. Introduce MCP incrementally around selected capabilities where the benefit is clear. Preserve underlying APIs for other consumers and avoid maintaining duplicate business rules.

For each decision, record which benefit is expected, how it will be measured and who owns the integration.
