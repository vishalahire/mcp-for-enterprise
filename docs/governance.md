# Governance and lifecycle

Use existing API, security and application governance as the foundation. Add a linked review for the agent-facing contract and its consumers.

## Ownership

| Owner | Accountable responsibilities |
| --- | --- |
| Domain and API owner | Business entitlements, service contract, data quality, transaction behavior and availability |
| MCP server owner | Tool semantics, catalog, dependencies, evaluations, compatibility and support |
| Gateway owner | Authentication, tool access, routing, quotas, telemetry and emergency disablement |
| Agent platform owner | Approved endpoints, runtime configuration, human interaction and trace propagation |
| Security and data owners | Identity, external data boundaries, supplier risk and retention |
| Business approver | Consequential changes within a defined scope of authority |

## Lifecycle

1. Describe the capability, consumers and decision rationale using the [server review template](../templates/server-review.md).
2. Link existing API approvals or review new and materially changed API exposure.
3. Review tool behavior, data classification, identity, hosting and side effects.
4. Assign an approved policy to each governed action.
5. Qualify the full runtime path and retain the test evidence.
6. Publish the approved consumer endpoint and version profile in the registry.
7. Monitor behavior, review material changes and retire unused endpoints and credentials.

For A2A delegation, register the peer's identity and skills, data boundary, timeout, cancellation and artifact retention. Apply governed-action policy to writes performed by the receiving agent.

## Registry record

Capture owner, support contact, environment, hosting party, gateway endpoint, upstream dependency, protocol and transport profile, approved consumers, tool names and versions, schema references, scopes, data classification, side effects, approval references, service objectives and retirement information.

Catalog metadata should refer to authoritative review records. A tool's self-declared safety annotations are inputs to review.

## Release evidence

| Area | Evidence to retain |
| --- | --- |
| Identity | Invalid, expired, wrong-audience and insufficient-scope requests are rejected |
| Entitlements | Cross-tenant and unauthorized object access are denied |
| Tool exposure | Hidden or disallowed tools cannot be invoked directly |
| Governed actions | Required approval is checked at execution and cannot be replayed for another operation |
| Bypass | Unapproved direct routes and alternative credentials are restricted |
| Resilience | Timeouts, disconnects, retries, duplicate writes and uncertain results are handled |
| Contract quality | Representative agents select tools correctly and complete bounded tasks |
| Observability | Correlated caller, gateway, approval and backend events with sensitive fields minimized |
| Operations | Disablement, rollback, credential rotation and incident ownership are exercised |

## Compatibility profile

Record client and SDK versions, gateway deployment mode and policy versions, server version, protocol version, transport, auth flow, primitives and extensions. Verify discovery, invocation, supported streaming and policy behavior together.

Vendor documentation can describe different compatibility levels for different policies. Approve a demonstrated combination. Requalify material upgrades.

## Change and incident handling

Reassess new tools, expanded writable scope, changed credentials, new data destinations, increased action limits and changed side effects. Apply proportionate review to deployment changes that preserve the approved contract.

On a control incident, disable affected tools or routes, revoke relevant approval authorizations and credentials, preserve evidence and reconcile uncertain transactions. Publish corrected catalog versions before re-enabling access.

[Governed actions](governed-actions.md) · [Research](research-and-sources.md).
