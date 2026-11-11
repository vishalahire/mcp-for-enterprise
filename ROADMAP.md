# Roadmap

The project starts with architecture research and reviewable enterprise patterns. Subsequent milestones build evidence through small reference implementations.

| Stage | Deliverable | Completion evidence |
| --- | --- | --- |
| Documentation foundation | System access and agent interaction trees, API/MCP comparison, reference architecture, governance, governed actions and source register | Published and internally linked guides |
| Contract design | Versioned server manifest and action-policy schema | Reviewed examples and validation rules |
| Read-only reference | Small MCP adapter over a synthetic HTTP service | Two clients demonstrate equivalent discovery and invocation |
| Governed update reference | Preview, durable approval and conditional execution | Changed arguments, expiry, concurrent updates and retries behave correctly |
| Gateway integration | A supported enterprise gateway configuration | Access enforcement and bypass tests |
| Vendor integration study | A documented supported vendor pattern | Identity, data boundary and failure behavior evaluated |
| Evaluation package | Repeatable contract and control checks | Published results tied to tested versions |

The current implementation status is the documentation foundation. Later stages are planned work. Select protocols and dependency versions when implementing each milestone and record the tested compatibility profile.
