#  Mini Project – Setting Up Secure Authentication to AWS API

##  Introduction

Hi! In this project, I set up **secure authentication** to AWS so I could use the **AWS CLI (Command Line Interface)** on a **Linux machine** to interact with AWS services like **EC2** and **S3**.

This setup allows me to write scripts that talk to AWS directly from my terminal. Here's how I did it step-by-step.

---

##  Project Objectives

* Set up an **IAM Role**, **Policy**, and **User** in AWS.
* Install and configure the **AWS CLI** on Linux.
* Understand **APIs** and how the AWS CLI uses them.
* Test authentication by listing AWS regions from the terminal.

---

##  Step 1: Create IAM Role

**What is an IAM Role?**
An IAM Role in AWS is like a set of permissions that can be given to users or services. I created a role that allows managing **EC2** and **S3**.

---

##  Step 2: Create IAM Policy

**What is an IAM Policy?**
A policy defines **what actions** are allowed on **which resources**. I created a custom policy that gives **full access** to EC2 and S3.

---

##  Step 3: Create IAM User

I created a user named **`automation_user`**. This user is the identity that my scripts and CLI will use to access AWS.

---

##  Step 4: Assign Role to User

I attached the role to **`automation_user`**, so the user inherits the permissions defined in the role.

---

## Step 5: Attach Policy to User

To make sure everything works, I also attached the custom policy directly to the user. This ensures the user can **fully manage EC2 and S3**.

---

##  Step 6: Generate Programmatic Access Credentials

I created **Access Key ID** and **Secret Access Key** for the `automation_user`. These are needed to let the AWS CLI connect to AWS services securely.

 I kept these credentials safe and **never shared them**.

---

##  Installing AWS CLI on Linux

**What is AWS CLI?**
The AWS Command Line Interface (CLI) lets me talk to AWS services from my **Linux terminal**, without using the web console.

### Steps I followed:

1. **Downloaded the installer**:

   ```bash
   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   ```

2. **Unzipped it**:

   ```bash
   unzip awscliv2.zip
   ```

3. **Installed AWS CLI**:

   ```bash
   sudo ./aws/install
   ```

4. **Checked the version**:

   ```bash
   aws --version
   ```

---

##  Configuring AWS CLI

I ran this command to start the setup:

```bash
aws configure
```

### I entered:

* **Access Key ID**
* **Secret Access Key**
* **Default Region** (e.g., `us-east-1`)
* **Output format** (`json` or `table`)

---

## Understanding APIs

An **API** (Application Programming Interface) allows two programs to talk to each other. In this case, the AWS CLI sends **API calls** to AWS services like EC2 and S3.

Each command like `aws ec2 describe-instances` is actually an API call that AWS understands.

This is what allows my shell scripts or CLI commands to **create**, **manage**, or **delete** AWS resources — all programmatically.

---

## Testing the Configuration

To check if my AWS CLI setup was successful, I ran:

```bash
aws ec2 describe-regions --output table
```

This command talks to the **EC2 API** and asks for a list of all AWS regions.

 It returned a nice table of regions, which confirmed that everything was working!

---

## Screenshot of Successful Output

Here’s a screenshot showing the output from the test command:

<img width="924" height="704" alt="AWS CLI CONFIRMATION" src="https://github.com/user-attachments/assets/ff82052d-897d-403b-a0e2-279f7268b812" />

---

## What I Learned

* IAM Users, Roles, and Policies are key to **secure access** in AWS.
* **Programmatic access** allows scripts to interact with AWS through the terminal.
* The **AWS CLI** makes it super easy to work with AWS services from Linux.
* Understanding how **API calls** work helps in automating cloud tasks.

---

## Final Thoughts

This setup was the foundation for automating AWS tasks with scripts. Now I can confidently write shell scripts that:

* Launch EC2 instances
* Create and manage S3 buckets
* Do much more, all from the terminal

---


