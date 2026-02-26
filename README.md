# SC60 Notes
## Breaking the perimeter: Anatomy of a Modern Intrusion
[ENISA Threat Landscape](https://www.enisa.europa.eu/sites/default/files/2025-11/ENISA%20Threat%20Landscape%202025.pdf)
Squat a domain, wait a few weeks.
[HTML Smuggling(https://attack.mitre.org/techniques/T1027/006/) -> download zip
Use a .lnk file with a PDF icon.
Hidden directory: .metadata
DLL sideloading with Chrome (not quite sure how it was able to put something in the same directory, have to ask).

Not a lot of work to prevent once the person is already inside the network.

The Honeypot: Just wait until one internal tool enumerates the servers and tries. [Anantis](https://anantis.io)

## iac, Kubernetes chez Piguet Galland
e-Banking project.

Infrastructure as code, Terraform.

- Pipeline must be the only way to deploy
- Can have temporary higher temporary privileges to troubleshoot

[tflint](https://github.com/terraform-linters/tflint), [checkov](https://www.checkov.io)

Switched to OpenTofu. Nice feature: state encryption.

How to deploy the applications: Containers
- SBOM via [syft](https://github.com/anchore/syft), [grype](https://github.com/anchore/grype)

How to run the containers: Docker has high privilege levels.

Use [Kaniko](https://github.com/GoogleContainerTools/kaniko) to build

[trivy](https://github.com/aquasecurity/trivy) to scan for vulnerabilities.

Standardized the build with CI/CD Components.

[Renovate](https://docs.renovatebot.com) for dependency updates.

ArgoCD on the Kubernetes cluster do deploy the containers.

Custom resource definition for external secrets. [External Secret Operator](https://external-secrets.io/latest/) 

How to store the secret for the secrets operator? [SOPS](https://github.com/getsops/sops)

For consistency: [Kyverno](https://kyverno.io)

Encrypt connection within Kubernetes between pods: [Istio](https://istio.io). Ambient mode - all connection is intercepted by ztunnel.

