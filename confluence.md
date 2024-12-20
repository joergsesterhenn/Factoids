# Confluence of Perceived Needs

A collection of perceived needs, those being features/functionality and their specifications using concrete examples.

This single document can be refined over time and placed into more specialized and useful documents.

To contribute, please submit a PR (Pull Request).

## Perceived Needs

### (Michele Sollecito)[https://www.linkedin.com/in/michelesollecito/]

(Initial with discussion)[https://www.linkedin.com/posts/michelesollecito_eventsourcing-eventstore-activity-7275623006314348544-AKcl]

(Follow up)[https://www.linkedin.com/posts/michelesollecito_eventsourcing-eventstore-activity-7275736782665617410-ItZ7]

1. We'd need a way to partition the facts, so that the ones regarding a given entity can be guaranteed to be processed in order. The trick is to do so in a way that allows the facts to pertain to more than 1 entity.
2. We should leverage the immutable nature of the facts to allow for efficient storage. A fact that references another fact shouldn't duplicate it, but point to it instead. A bit like persistent immutable collections.
3. A sequence number is an easy but location-dependent way to prove causality. Referencing predecessors would allow clients to work without communicating each new fact individually to the server, both increasing throughput and obtaining resilience to network partitions. Resolving conflicts would also be easy this way. A message would contain a DAG of facts, referring to pre-known facts.
4. The binary format chosen matters a lot, as schema compatibility and evolution are paramount and hard. Dealing with old historical events is a pain.
5. The latency introduced can't be too significant e.g. by polling on the client side. And it can't be a single instance that writes all new facts. BookKeeper might be a good solution for this second requirement.
6. Observability and Auditability
- We should capture the invocation/execution context as part of an event context. And that's the easy part.
- The hard part is for the framework to know the structure and the meaning of this context, to provide out-of-the-box observability. We need either a standard, or some sort of description language. And both are hard.
- It would have to support multiple tenants and customers, user and service accounts, different authentication methods with token and session information, authorisation roles and scopes, impersonation, etc.

### (Flavius Aspra)[https://www.linkedin.com/in/flavius-a-0b9136b4/]

This would be useful if it would be also aware of the use cases the application implements, the scenarios, and connected to the infrastructure (e.g. software load balancer, OpenTracing-aware)

## Specifications by Example

Specifications must state the summary of the need, its purpose, and at least one concrete example.

- Concrete means not abstract; it must give a realistic example of what the feature/functionality does.
- Examples can be written as:
  - Simple (clear and understandable) prose
  - Numbered steps
  - Given-When-Then

### RENAME Specification and Example 1

### RENAME Specification and Example 2

### RENAME Specification and Example 3
