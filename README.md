# CI/CD Pipeline Project

This project implements a CI/CD pipeline using GitHub Actions, Docker, Terraform, and AWS services. The pipeline builds a Docker image, pushes it to Amazon ECR, and deploys it to an ECS service using Fargate.

## Project Structure

```
my-cicd-project
├── .github
│   └── workflows
│       └── deploy.yml
├── terraform
│   ├── variables.tf
│   ├── outputs.tf
│   ├── ecr.tf
│   ├── ecs.tf
│   ├── vpc.tf
│   └── providers.tf
├── docker
│   └── Dockerfile
├── src
│   └── app
├── scripts
│   └── deploy.sh
└── README.md
```


## Setup Instructions

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd my-cicd-project
   ```

2. **Configure AWS credentials:**
   Ensure that your AWS credentials are configured in your environment. You can use the AWS CLI to configure them.

3. **Deploy the infrastructure:**
   Navigate to the `terraform` directory and run:
   ```bash
   terraform init
   terraform apply
   ```

4. **Build and push the Docker image:**
   You can manually build and push the Docker image using the following commands:
   ```bash
   cd docker
   docker build -t <image-name> .
   docker tag <image-name>:latest <aws_account_id>.dkr.ecr.<region>.amazonaws.com/<repository-name>:latest
   docker push <aws_account_id>.dkr.ecr.<region>.amazonaws.com/<repository-name>:latest
   ```

5. **Run the deployment script:**
   Execute the deployment script to automate the process:
   ```bash
   cd scripts
   ./deploy.sh
   ```

## Usage

After deployment, your application will be running on AWS ECS. You can access it via the load balancer URL provided in the outputs of the Terraform configuration.

## License

This project is licensed under the MIT License.
