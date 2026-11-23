# CI Pipeline Examples

The active GitHub Actions workflow is stored at `.github/workflows/validate-kubernetes.yml`, as required by GitHub. It validates the sample Helm chart and renders both Kustomize overlays on pushes and pull requests.

Add image build, scanning, signing, and deployment stages only after selecting the registry and deployment trust model. Store credentials in a managed secret store or use short-lived workload identity; never commit them.
