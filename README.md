# Setup Guide

## login 
chmod 400 "py.pem"
ssh -i "py.pem" ubuntu@18.208.190.58

## AWS CLI Installation

To install the AWS CLI, follow the instructions in the official AWS documentation:

[Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

### Steps:

1. **Download the AWS CLI Installer**:
    ```bash
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    ```

2. **Unzip the Installer**:
    ```bash
    sudo apt update
    sudo apt install unzip
    unzip awscliv2.zip
    ```

3. **Run the Installer**:
    ```bash
    sudo ./aws/install
    ```

4. **Verify the Installation**:
    ```bash
    aws --version
    ```

## Boto3 Installation

Here are the steps to create a virtual environment and install `boto3` within it:

1. **Ensure Python and `venv` module are installed**:
    ```bash
    sudo apt update
    sudo apt install python3 python3-venv
    ```

2. **Create a virtual environment**:
    ```bash
    python3 -m venv myenv
    ```

3. **Activate the virtual environment**:
    ```bash
    source myenv/bin/activate
    ```

4. **Install `boto3` using `pip` within the virtual environment**:
    ```bash
    pip install boto3
    ```

5. **To deactivate the virtual environment**:
    ```bash
    deactivate
    ```

## AWS Configuration

After installing the AWS CLI, configure your AWS credentials:

1. **Configure AWS CLI**:
    ```bash
    aws configure
    ```

    You will be prompted to enter your AWS Access Key ID, Secret Access Key, region, and output format.

## Checking AWS EC2 Instances

To check the list of EC2 instances, use the following command:

```bash
aws ec2 describe-instances --query 'Reservations[*].Instances[*].{ID:InstanceId,State:State.Name}' --output table
