# Production Readiness: Review Notes

The example demonstrates three replicas, rolling updates with no planned unavailability from the Deployment strategy, non-root container execution, dropped Linux capabilities, probes, resource requests/limits, and a PodDisruptionBudget.

These settings are examples, not a production guarantee. Validate image availability, capacity, security requirements, disruption behavior, and application-specific probes in the target environment. A PDB only constrains supported voluntary disruptions; it does not prevent node failure or replace redundancy, monitoring, and tested recovery.
