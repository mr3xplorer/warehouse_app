# warehouse_app
Warehouse management application using PHP, AWS RDS (MySQL), EC2 (Ubuntu), and Terraform for infrastructure as code (IaC).

## Introduction

This application helps manage inventory, track shipments, and streamline warehouse operations using scalable and reliable AWS services.

## Architecture

![Architecture Diagram](WMS_AWS.jpg)

### Production

- **PHP Application**: Hosted on an EC2 instance (Ubuntu).
- **Database**: MySQL on AWS RDS.
- **Infrastructure**: Managed with Terraform.

### CI/CD for Developers

- **Elastic Beanstalk**: For deploying and managing the PHP application.
- **CodePipeline**: Automates CI/CD.
- **GitHub**: Hosts the source code repository.

## Prerequisites

- AWS Account
- AWS CLI configured
- Terraform installed
- SSH key pair for EC2
- PHP and Composer installed locally

## Setup

### Terraform Setup

1. **Clone the repository**:
    ```sh
    git clone https://github.com/mr3xplorer/warehouse_app.git
    cd warehouse_app/terraform_code
    ```

2. **Initialize Terraform**:
    ```sh
    cd terraform
    terraform init
    ```

3. **Update Terraform variables** in `variables.tf`.

4. **Apply Terraform configuration**:
    ```sh
    terraform apply
    ```
    Note the EC2 instance IP and RDS endpoint.

### Application Setup

1. **SSH into the EC2 instance**:
    ```sh
    ssh -i /path/to/your-key.pem ubuntu@<ec2-instance-ip>
    ```

2. **Install dependencies**:
    ```sh
    sudo apt update
    sudo apt install -y apache2 php php-mysql libapache2-mod-php
    ```

3. **Clone the repository on EC2**:
    ```sh
    git clone https://github.com/mr3xplorer/warehouse_app.git
    cd warehouse_app
    ```

4. **Configure the application** in `config.php`.

5. **Deploy the application**:
    ```sh
    sudo cp -r * /var/www/html/
    sudo systemctl restart apache2
    ```
