# aws-proton-workshop-templates

AWS Proton templates for use with pulumi/workshops/aws-proton.

These templates are based on <https://github.com/adamjkeller/proton-codebuild-provisioning-examples/tree/main/pulumi>.

## Repo Structure

The repo contains the following directories:

- `environment-vpc/v1` contains a proton environment template that contains a VPC. In some organizations, this infrastructure might be managed by a centralized Network Team.
- `environment-k8s/v1` contains a proton Environment template that contains an EKS cluster. In some organizations, this infrastructure might be managed by a centralized Platform Team.
- `service-k8s-app/v1` contains a Proton service template to deploy an application on to our Kubernetes cluster. This template would be consumed by application teams to launch their services.

Each Proton template differs from a plain Pulumi program in the following ways:

- Each template contains a `schema` directory and a `template` directory.
- The `schema` directory contains a `schema.yaml` file that contains the inputs to the template. These inputs will be mapped to the Proton console UI.
- The `template` directory contains the usual contents of a Pulumi program, plus a `manifest.yaml` file that contains the instructions that will be executed by CodeBuild, similar to a typical CodeBuild `buildspec.yaml` file except with instructions to both provision and deprovision the infrastructure in the Pulumi program.
