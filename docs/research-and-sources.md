# Industry research and primary sources

Research baseline — 10 November 2026.

This register separates published specifications, vendor capabilities and project recommendations. Product documentation changes. Recheck it when selecting versions for a deployment.

## Standards and design guidance

| Source | Documented contribution | Application in this project |
| --- | --- | --- |
| MCP project | Protocol, tools, authorization and security guidance | Standard discovery and invocation with verified identity and explicit capability selection |
| A2A project | Agent discovery, messages, tasks and artifacts | Assess A2A when delegating work to an independently operated agent |
| OpenAPI Initiative | Language-independent descriptions of HTTP APIs | Use an API contract to seed a curated tool mapping |
| Anthropic engineering | Task-oriented tools, concise responses and evaluations | Design and evaluate a bounded tool catalog |

The decision tree is an architectural synthesis. A protocol specification establishes interoperability requirements, while organizational policy determines approved use.

- [MCP specification](https://modelcontextprotocol.io/specification/2026-07-28)
- [MCP tools](https://modelcontextprotocol.io/specification/2026-07-28/server/tools)
- [MCP authorization](https://modelcontextprotocol.io/specification/2026-07-28/basic/authorization)
- [MCP security best practices](https://modelcontextprotocol.io/docs/2026-07-28/tutorials/security/security_best_practices)
- [A2A specification](https://a2a-protocol.org/latest/specification/)
- [A2A and MCP roles](https://a2a-protocol.org/latest/blog/2026/08/27/a-new-chapter-for-a2a-joining-the-agentic-ai-foundation/)
- [OpenAPI Specification 3.2.1](https://spec.openapis.org/oas/v3.2.1.html)
- [Anthropic on writing effective tools](https://www.anthropic.com/engineering/writing-tools-for-agents)

## System access and agent interaction decisions

Focused review — 11 November 2026.

The [system access decision tree](decision-tree.md) asks how an agent should obtain current information from an internal or third-party system through API tools, existing MCP or a new MCP interface. The [comparison guide](api-vs-mcp.md) explains why existing APIs remain valid and where MCP adds value. The [agent interaction tree](agent-interaction-decision-tree.md) separately evaluates API, MCP and A2A when the provider is another agent.

| Primary evidence | Documented contribution | Project interpretation |
| --- | --- | --- |
| OpenAI function calling | Applications can execute defined tools against external systems | An API-backed tool is a valid integration option |
| OpenAI MCP guide | Remote MCP integration, tool filtering and approvals | MCP is another supported integration path, requiring explicit controls |
| Microsoft API Management | Selected REST operations can be exposed as MCP tools | Existing APIs can remain authoritative beneath an MCP interface |
| MCP tools and security guidance | Standard tool interface and security responsibilities | MCP does not itself guarantee business authorization or freshness |
| Anthropic tool engineering | Tool selection, concise results, descriptions and evaluations | Tool quality must be assessed separately from transport choice |
| A2A comparison | Agent collaboration and tool integration are complementary | Choose the interaction contract before selecting the peer protocol |

The preference for the simplest qualified existing path, the comparative cost model, freshness gates and scenario outcomes are project recommendations. They are not normative protocol rules or claims about enterprise adoption prevalence. Concur-like examples are hypothetical; no vendor MCP availability or tenant entitlement is asserted.

- [OpenAI function calling](https://developers.openai.com/api/docs/guides/function-calling)
- [OpenAI MCP servers](https://developers.openai.com/api/docs/guides/tools-connectors-mcp)
- [Microsoft API to MCP exposure](https://learn.microsoft.com/en-us/azure/api-management/export-rest-mcp-server)
- [Anthropic writing effective tools](https://www.anthropic.com/research/writing-tools-for-agents)
- [MCP security guidance for the 2025-11-25 profile](https://modelcontextprotocol.io/docs/2025-11-25/tutorials/security/security_best_practices)
- [A2A and MCP comparison](https://a2a-protocol.org/latest/topics/a2a-and-mcp/)

Anthropic's [building effective agents](https://www.anthropic.com/research/building-effective-agents) and [multi-agent research system](https://www.anthropic.com/research/multi-agent-research-system) provide additional architectural context for evaluating reasoning, coordination and resource costs. Historical examples and workload-specific results are not universal performance guarantees.

## Provider implementation examples

| Provider | Documented behavior | Deployment question |
| --- | --- | --- |
| OpenAI | MCP tool filtering and approval request/response handling | Which tools require approval and how is the request associated with the authorized execution? |
| Anthropic | Managed Agents permission policies offer allow, ask and automatic evaluation, with MCP toolsets defaulting to ask in the reviewed documentation | Does the selected product and deployment support the required policy? The reviewed capability is beta |
| Google ADK | MCP tools and action-confirmation mechanisms | Which tool types, transports and runtime versions support the required confirmation flow? |
| Microsoft Azure API Management | Selected REST operations can be exposed as MCP tools | Does the bridge support the required capabilities and streaming behavior? |
| Google Cloud Apigee | MCP access can be controlled with API products | How are tool visibility and invocation permissions aligned? |
| MuleSoft | API to MCP Bridge and gateway policies for tool access | Which installed versions support the full protocol and policy combination? |
| UnifyApps | Publishing MCP/A2A capabilities and consuming external MCP through its connector | Verify publishing and consuming independently, including auth and transport |
| Palantir | External Ontology MCP exposure, native action submission criteria and specific approval workflows | Which capabilities exist in the enrollment, and which business actions require additional workflow implementation? |

These examples illustrate available mechanisms. Enterprise adoption prevalence and production readiness require additional evidence.

- [OpenAI MCP servers](https://developers.openai.com/api/docs/guides/tools-connectors-mcp)
- [Anthropic permission policies](https://platform.claude.com/docs/en/managed-agents/permission-policies)
- [Google ADK MCP tools](https://adk.dev/tools-custom/mcp-tools/)
- [Google ADK action confirmations](https://adk.dev/tools-custom/confirmation/)
- [Microsoft API to MCP exposure](https://learn.microsoft.com/en-us/azure/api-management/export-rest-mcp-server)
- [Apigee MCP tool access](https://docs.cloud.google.com/apigee/docs/api-platform/apigee-mcp/manage-mcp-tool-access)
- [MuleSoft MCP Bridge](https://docs.mulesoft.com/api-manager/latest/create-instance-task-mcp-bridge)
- [Omni Gateway MCP access policies](https://docs.mulesoft.com/gateway/latest/policies-mcp-access-control-together)
- [Exchange publication and gateway routing](https://docs.mulesoft.com/agent-visualizer/view-and-navigate-agent-network)
- [UnifyApps MCP and A2A servers](https://www.unifyapps.com/docs/unify-agentic-ai/mcp-a2a-servers)
- [UnifyApps MCP client connection and connector direction](https://www.unifyapps.com/docs/unify-agentic-ai/mcp-client-connection)
- [Palantir AIP Chatbot Studio](https://www.palantir.com/docs/foundry/chatbot-studio)
- [Palantir Ontology MCP announcement](https://www.palantir.com/docs/foundry/announcements/2026-05)

## Consequential actions

OpenAI's approval request lifecycle and Anthropic's permission policies demonstrate runtime gating. Palantir submission criteria demonstrate checking business context where an action executes. Palantir's Approvals application documents specific administrative and governance workflows, including access requests and Ontology proposals. Verify coverage before adopting it for a business transaction.

MCP tool annotations are advisory. An enterprise should verify actual side effects and maintain its approved classification. The approval binding, durable workflow, idempotency and reconciliation design in this project is a proposed application architecture.

- [MCP tool annotation semantics and trust warning](https://kotlin.sdk.modelcontextprotocol.io/kotlin-sdk-core/io.modelcontextprotocol.kotlin.sdk.types/-tool-annotations/index.html)
- [Palantir action submission criteria](https://www.palantir.com/docs/foundry/action-types/submission-criteria)
- [Palantir action permissions](https://www.palantir.com/docs/foundry/action-types/permissions)
- [Palantir Approvals](https://www.palantir.com/docs/foundry/approvals/overview)

## Version qualification

The MCP project published the 2026-07-28 revision with a stateless protocol core. Existing deployments may use earlier profiles. Select a version supported by all required components and record the tested combination.

The reviewed MuleSoft MCP Support page lists 2025-06-18 and earlier. Its Schema Validation 1.3.0 release notes describe recognition fixes for methods from 2025-11-25. These pages address different policies, so neither establishes compatibility of a complete deployment with the newest protocol.

The reviewed UnifyApps publishing documentation describes an SSE connection. Check the active product version and test its actual transport through the selected gateway.

- [MCP 2026-07-28 release](https://blog.modelcontextprotocol.io/posts/2026-07-28/)
- [Omni MCP Support policy](https://docs.mulesoft.com/gateway/latest/policies-included-mcp-support)
- [MCP Schema Validation release notes](https://docs.mulesoft.com/release-notes/gateway/policies/mcp-schema-validation-release-notes)

## Maintaining the research

For each update, retain the source URL, review date, affected claim, version scope and any demonstrated compatibility evidence. Mark implementation assumptions explicitly. Prefer specifications and vendor documentation for product behavior.
