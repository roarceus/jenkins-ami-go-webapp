# Jenkins AMI Build and CI/CD with Packer and GitHub Actions

## Overview
This project outlines the process for creating a custom Amazon Machine Image (AMI) for Jenkins using Packer. The AMI will include all necessary components for Jenkins, including plugins but excluding configuration. Additionally, the project implements a CI/CD pipeline using GitHub Actions to automate the AMI build and registration process upon repository updates.

## Requirements

### AMI Build
1. **Source Image**: Use Ubuntu 24.04 LTS.
2. **Private AMI**: Ensure the AMI is private and accessible only to your team.
3. **ROOT AWS Account**: Perform all AMI builds in the root AWS account.
4. **Default VPC**: The AMI build should utilize the default VPC in your AWS account.
5. **Jenkins Setup**:
   - Install Jenkins.
   - Install necessary plugins (excluding configuration).
6. **Reverse Proxy**:
   - Use Nginx as a reverse proxy for Jenkins.

### CI/CD Pipeline
1. **Trigger**: Any changes pushed to the repository should trigger the pipeline.
2. **Build**: Automate the Packer build process.
3. **Registration**: Register the newly built private AMI in the ROOT AWS account.

## Notes
- **Private AMI**: Use IAM policies to ensure AMI visibility is restricted to your team.
- **IAM Roles**: Attach required IAM roles to the GitHub Actions runner or local environment to allow AMI creation.

## Outputs
- A private AMI in the ROOT AWS account.
- Jenkins is set up and ready for configuration after launching an EC2 instance.

## References
- [Packer Documentation](https://www.packer.io/docs)
- [Jenkins Documentation](https://www.jenkins.io/doc/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
