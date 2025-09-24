# Terraform AWS Infrastructure as Code

This repository holds the Terraform code for managing AWS infrastructure.

## Project Structure

The project is organized into two main directories: `modules` and `environments`.

```
.
├── modules
│   ├── ec2
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   ├── lambda
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   ├── rds
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   └── vpc
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
├── environments
│   ├── dev
│   │   └── main.tf
│   ├── staging
│   │   └── main.tf
│   └── prod
│       └── main.tf
└── main.tf
```

### Modules

The `modules` directory contains reusable Terraform modules for creating specific AWS resources. Each module is self-contained and defines a piece of infrastructure.

-   **`ec2`**: This module is responsible for creating and configuring Amazon EC2 instances.
-   **`lambda`**: This module handles the deployment and configuration of AWS Lambda functions.
-   **`rds`**: This module is used to provision and manage Amazon RDS database instances.
-   **`vpc`**: This module sets up a Virtual Private Cloud (VPC) with its associated networking components like subnets, route tables, and security groups.

### Environments (Live Stacks)

The `environments` directory represents the different deployment environments, often referred to as "live stacks." Each subdirectory corresponds to a specific environment:

-   **`dev`**: The development environment.
-   **`staging`**: The staging or pre-production environment.
-   **`prod`**: The production environment.

Each environment's `main.tf` file is responsible for composing the infrastructure for that specific stack by calling the reusable modules from the `modules` directory. This allows for consistent infrastructure across environments while allowing for environment-specific configurations (e.g., different instance sizes or database capacities) through variables.

## How to Use

1.  Navigate to the desired environment directory (e.g., `cd environments/dev`).
2.  Initialize Terraform: `terraform init`
3.  Review the execution plan: `terraform plan`
4.  Apply the changes: `terraform apply`

