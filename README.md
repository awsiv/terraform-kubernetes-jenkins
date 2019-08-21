# terraform-kubernetes-jenkins

Terraform module for deploying Jenkins on Kubernetes

## Usage

```terraform
module "this" {
  source              = "github.com/jjno91/terraform-kubernetes-jenkins?ref=master"
  jenkins_volume_id   = "vol-abc123"
  jenkins_volume_size = "50"
}
```

## Configuring Kubernetes Cloud

Jenkins will be accessible inside the Kubernetes cluster from the DNS <identifier>.<identifier>.svc.cluster.local

This DNS will need to be entered in the "Jenkins URL" config field for Kubernetes Cloud definition in order for K8S based JNLP agents to reach Jenkins

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| identifier | (optional) Used to generate namespace and name resources | string | `"jenkins"` | no |
| jenkins\_image | Jenkins container image | string | `"jenkins/jenkins:latest"` | no |
| jenkins\_version | (optional) https://hub.docker.com/r/jenkins/jenkins/tags | string | `"latest"` | no |
| jenkins\_volume\_id | (required) Jenkins persists its data on disk and needs a static EBS volume ID in order to maintain state | string | `""` | no |
| jenkins\_volume\_size | (required) Jenkins volume size in gigabytes | string | `""` | no |
| jnlp\_node\_port | (optional) JNLP port used by Jenkins agents | string | `"30001"` | no |
| jnlp\_port | (optional) JNLP port used by Jenkins agents | string | `"50000"` | no |
| labels | (optional) Additional labels applied to all resources | list | `[]` | no |
| volume\_availability\_zone | (required) Jenkins must be deployed to the same zone as its persistent data volume | string | `""` | no |
| web\_node\_port | (optional) Jenkins web port internal to the Jenkins container | string | `"30000"` | no |
| web\_port | (optional) Jenkins web port internal to the Jenkins container | string | `"8080"` | no |

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

