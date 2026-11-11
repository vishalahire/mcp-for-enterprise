# MCP for Enterprise

Practical architecture guidance and governance patterns for adopting the Model Context Protocol across enterprise applications, SaaS products and agent platforms.

This project helps architects and engineering teams choose an integration approach, expose useful tools, and govern consequential actions. It brings together primary-source research, reference architectures and reusable review templates.

**Status — documentation foundation.** The current release contains design guidance and illustrative examples. Runtime implementations and automated conformance checks are planned.

## Start here

| Your question | Guide |
| --- | --- |
| Should my agent use an existing API, reuse MCP or introduce MCP for current system information? | [System access decision tree](docs/decision-tree.md) |
| Why would I need MCP when APIs already exist? | [API versus MCP comparison](docs/api-vs-mcp.md) |
| How should my agent interact with another agent through API, MCP or A2A? | [Agent interaction decision tree](docs/agent-interaction-decision-tree.md) |
| How do gateways, adapters and existing APIs fit together? | [Reference architecture](docs/reference-architecture.md) |
| How should tools be reviewed, registered and operated? | [Governance and lifecycle](docs/governance.md) |
| How do I govern create, update and delete actions? | [Governed actions](docs/governed-actions.md) |
| What do the specifications and vendors actually document? | [Industry research and sources](docs/research-and-sources.md) |
| What should a review record capture? | [Server review template](templates/server-review.md) and [action policy template](templates/action-policy.md) |
| What will the project build next? | [Roadmap](ROADMAP.md) |

## Approach

- Treat existing APIs as valid agent tools; adopt MCP for demonstrated interoperability, reuse or management value.
- Qualify API and MCP paths independently before selecting one for each capability.
- Choose API, MCP or A2A separately when the provider is another agent.
- Specify source freshness, security boundaries and measured performance budgets.
- Reuse domain services and managed APIs when exposing MCP tools.
- Design tools around bounded business tasks with clear inputs and outputs.
- Apply enterprise policy consistently across custom and vendor-hosted servers.
- Bind human approval to the actual operation and enforce it before execution.
- Qualify the complete client, gateway and server combination.

Recommendations describe a proposed enterprise operating model. Normative protocol requirements remain in the linked specifications. Product capabilities depend on version, deployment mode and tenant configuration.

## Scope

The reference landscape includes existing HTTP APIs, hosted SaaS integrations, container-hosted adapters, API management, an MCP gateway and registry, and heterogeneous agent runtimes. Organizations can map these roles to their own products.

The research baseline is 10 November 2026, with the system access and agent interaction decision models reviewed on 11 November 2026. Sources and compatibility considerations are maintained in the [research guide](docs/research-and-sources.md).

## License

[Apache License 2.0](LICENSE).
