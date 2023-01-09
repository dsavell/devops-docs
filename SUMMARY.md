# Table of contents

* [Welcome!](README.md)

## Patterns

* [Terraform](patterns/terraform/README.md)
  * [Style Guide](patterns/terraform/style-guide.md)
  * [Root Module](<patterns/terraform/README (1).md>)
    * [Code Structure](patterns/terraform/code-structure/README.md)
      * [Multiple Manifests Multi Environments](patterns/terraform/code-structure/root-module-multiple-manifests.md)
      * [Single Manifest Multi-Environment](patterns/terraform/code-structure/root-module-single-manifest.md)
    * [CI/CD Setup](patterns/terraform/root-module/ci-cd-setup/README.md)
      * [Azure DevOps](patterns/terraform/root-module/ci-cd-setup/azure-devops.md)
      * [GitLab](patterns/terraform/root-module/ci-cd-setup/gitlab.md)
      * [GitHub](patterns/terraform/root-module/ci-cd-setup/github.md)
  * [Child Module](patterns/terraform/child-module/README.md)
    * [Code Structure](patterns/terraform/child-module/code-structure.md)
    * [CI/CD Setup](patterns/terraform/child-module/ci-cd-setup/README.md)
      * [Azure DevOps](patterns/terraform/child-module/ci-cd-setup/azure-devops.md)
      * [GitLab](patterns/terraform/child-module/ci-cd-setup/gitlab.md)
      * [GitHub](patterns/terraform/child-module/ci-cd-setup/github.md)
* [Source Code Management](patterns/source-code-management.md)
* [Kubernetes](patterns/kubernetes/README.md)
  * [Helm](patterns/kubernetes/helm.md)
* [Secret Management](patterns/secret-management/README.md)
  * [User Secret Management](patterns/secret-management/user-secret-management.md)
  * [System Secret Management](patterns/secret-management/system-secret-management.md)
