# Instana Dynamic Focus Filtering

The Instana Dynamic Focus search bar is displayed on the Infrastructure Map page and is used for specifying the scope for events and alerts. It provides a robust search and filter function capable of searching through all data contexts simultaneously, enabling a strong system-wide understanding.

## Key Capabilities

### Dynamic Graph
A cohesive model that contains physical and logical components with all historical attributes and metrics, including distributed traces and events. Dynamic Focus filters the graph to provide specific subviews and focus.

### Auto Discovery
The Instana agent automatically discovers all components and their dependencies in real-time, adapting any saved filter to the current system and application status without manual changes or configuration.

### Incidents
Instana incidents are based on KPIs and machine learning, providing condensed information about incidents, including dependencies to services, traces, and physical components. Dynamic Focus can filter only the components that are part of a particular incident.

## Query Examples

- **Filter by Infrastructure**: `entity.type:tomcat`
- **Filter by JVM Version**: `entity.jvm.version:1.8.*`
- **Filter by Incidents**: `event.state:open event.type:incident`

## Lucene Query Syntax

Instana uses Lucene query syntax to build complex queries. Queries proceed from a field to a field modifier and then to a quantifier. Example: `entity.type:tomcat`.

### Default Operator
The `AND` operator is the default conjunction operator. For example, `entity.type:tomcat event.state:open` is equivalent to `entity.type:tomcat AND event.state:open`.

### Complex Subqueries
Lucene query syntax and Dynamic Focus queries do not support complex Boolean terms. For example, `entity.kubernetes.namespace:my-namespace AND NOT (entity.kubernetes.pod.name:my-name AND event.text:"ContainersNotReady")` does not yield the expected results.

### Auto-complete
The search bar supports autocompletion for search fields and highlights Lucene query terms while typing.

## Known Limitations

- **Syntax Constraints**: Specific rules for whitespace, multiple keywords, and negations.
- **Query Limitations**: Issues with hyphens in `event.text` and certain Kubernetes keyword selections.

## FAQ

- **Using Wildcard (*)**: Inside double quotation marks ("") does not yield expected results.
- **Search Result Counts**: Might seem inconsistent due to the visibility of entities.
- **Default Fields**: Searches target the current context to provide meaningful results.

For more detailed information, visit the [IBM Instana documentation](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-filtering-dynamic-focus).
