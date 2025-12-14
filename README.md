# CICD-MultiStage-YAML-Pipeline
![CICD Trunk Based Branching Strategy for Infra Provisioning Diagram](https://github.com/devopsengineerakansha/CICD-MultiStage-YAML-Pipeline/blob/main/Infra%20Provisioning%20Trunk%20Based%20Branching%20Strategy.svg)

<br>In this diagram, I am showing a complete Terraform workflow using GitHub, Trunk-Based Branching Strategy, and separate Dev/Prod pipelines. 

All infrastructure code lives in a single Infra repository, where no one can push directly to the main branch every change must go through a feature branch and a Pull Request with at least one reviewer, ensuring governance and code quality. Inside the repo, we maintain clean environment separation with individual Dev and Prod folders containing their own main.tf, variables.tf, provider.tf, and terraform.tfvars files. 

Each environment uses its own remote backend (devstorage and prodstorage) to securely store Terraform state. Once changes are merged to main, the respective CI/CD pipeline is triggered: the Dev pipeline runs init, plan, and apply for the Dev folder, and the Prod pipeline does the same for the Prod folder, with apply allowed only on main. 

This setup ensures consistent deployments, strong security, proper isolation between environments, and a fully automated, review-driven Infrastructure-as-Code workflow.
