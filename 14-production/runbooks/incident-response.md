# Incident Response Tabletop

Use this guide for a simulated incident. Do not make changes to production during a training exercise.

## Scenario

The service's error rate rises following a deployment. Some replicas are ready, but user requests are failing.

## Response steps

1. **Declare and coordinate:** Assign incident lead, communications owner, and technical responders.
2. **Assess impact:** Identify affected users, regions, operations, and start time.
3. **Check signals:** Review SLO dashboards, alert history, recent Events, logs, traces, and rollout status.
4. **Stabilize:** Choose the lowest-risk mitigation, such as pausing rollout or rolling back, using the service's approved procedure.
5. **Verify:** Confirm user-facing health, error rate, latency, and replica readiness recover.
6. **Communicate:** Share concise status updates and next update time through the approved channel.
7. **Recover:** Confirm the system is stable and all temporary mitigations are tracked.
8. **Learn:** Write a blameless timeline, contributing factors, detection gaps, and prioritized follow-up actions.

## Record

- Incident lead:
- Start/end time:
- Customer impact:
- Detection source:
- Mitigation and verification:
- Follow-up owner and due date:
