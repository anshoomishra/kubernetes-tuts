# Troubleshooting: Diagnosis Guide

| Example | Evidence to find | Root cause | General corrective action |
|---|---|---|---|
| `crash-loop.yaml` | Restart count increases; current and previous logs show exit | The process exits with code 1 | Correct the command/application behavior; confirm exit status and logs |
| `bad-image.yaml` | `ImagePullBackOff` and Events show failed pull | Image reference is intentionally invalid | Correct the image name/tag or registry credentials |
| `missing-config.yaml` | Pod Events report missing ConfigMap | The referenced ConfigMap is absent | Create the intended ConfigMap or fix the reference |
| `unschedulable.yaml` | Pod is Pending; Events report insufficient resources | CPU/memory requests exceed node capacity | Right-size requests or provide sufficient cluster capacity |

After applying a fix, verify the Pod reaches the intended state and inspect Events again. Do not hide failures by repeatedly restarting or deleting resources before collecting evidence.

For general incidents, record timeline, user impact, signals, root cause, mitigation, recovery verification, and follow-up prevention work.
