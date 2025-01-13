# AWS Identity and Access Management (AWS IAM)

AWS Identity and Access Management (IAM) enables secure access control to AWS services and resources. IAM allows you to manage users, groups, permissions, and roles, ensuring secure and fine-grained access to resources in your AWS account.

## IAM: Users & Groups

- **Users**: Represent individual accounts in AWS, typically for people or applications requiring AWS access. Each user has a unique name.
- **Groups**: Collections of users. Assign permissions to groups rather than individual users to simplify management. Users inherit permissions assigned to their groups.

## IAM: Permissions

Permissions determine the actions that users or groups can perform on AWS resources. Permissions are defined using **policies**.

## IAM Policies Inheritance

- Users inherit permissions assigned to the groups they belong to.
- Multiple policies (attached to a user, group, or role) are combined to determine the effective permissions.
- Deny statements take precedence over Allow statements in cases of conflicts.

## IAM Policies Structure

IAM policies are JSON documents consisting of:
- **Version**: Policy language version.
- **Statement**: Defines one or more permissions, each including:
  - **Effect**: Allow or Deny.
  - **Action**: Specific actions to allow or deny (e.g., `s3:PutObject`).
  - **Resource**: Resources to which the actions apply (e.g., an S3 bucket ARN).
  - **Condition** (optional): Specifies additional constraints (e.g., time of access).

Example Policy:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::example-bucket"
    }
  ]
}
```

## IAM – Password Policy

Defines rules for passwords, such as:
- Minimum length
- Requirement for numbers, uppercase letters, or special characters
- Password expiration
- Preventing password reuse

## Multi-Factor Authentication (MFA)

MFA enhances security by requiring users to provide a second factor (e.g., a code) in addition to their password.

### MFA Devices Options in AWS

- Virtual MFA devices (e.g., Google Authenticator)
- U2F security keys (e.g., YubiKey)
- Hardware MFA devices

## How Can Users Access AWS?

- **AWS Management Console**: Browser-based graphical interface.
- **AWS CLI (Command Line Interface)**: Tool to manage AWS services via commands.
- **AWS SDKs (Software Development Kits)**: Libraries for programmatic access to AWS services.

## What’s the AWS CLI?

The AWS CLI is a command-line tool for managing AWS services, supporting automation and scripting.

## What’s the AWS SDK?

AWS SDKs are language-specific libraries that allow developers to interact with AWS services programmatically. Examples include SDKs for Python (Boto3), Java, .NET, and more.

## IAM Roles for Services

IAM roles allow AWS services to interact with other AWS resources securely. Roles provide temporary security credentials, reducing the need for permanent access keys.

## IAM Security Tools

- **IAM Access Analyzer**: Identifies resources shared with external entities.
- **Credential Reports**: Lists account-level credentials and their status.
- **IAM Policy Simulator**: Tests and validates policy configurations.

## IAM Guidelines & Best Practices

1. Follow the principle of **least privilege**.
2. Use **groups** to manage permissions.
3. Enable **MFA** for all accounts.
4. Regularly review **IAM policies**.
5. Avoid using the root account for daily operations.
6. Rotate security credentials regularly.
7. Monitor account activity using **CloudTrail**.

---

This document provides an overview of AWS IAM topics and serves as a reference for managing secure access to AWS resources effectively.
