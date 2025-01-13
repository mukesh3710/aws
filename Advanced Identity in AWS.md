# Advanced Identity in AWS
AWS offers advanced identity management features to secure and organize access to resources efficiently across multiple accounts and environments.

---

## Organizational Units (OUs)
- Logical grouping of AWS accounts within AWS Organizations.
- Simplifies management by applying Service Control Policies (SCPs) at the OU level.
- Use cases: Environment segregation (e.g., development, testing, production) or departmental organization.

---

## AWS Organizations
- Centralized management of multiple AWS accounts.
- **Key Features:**
  - Manage billing and budgets centrally.
  - Use SCPs to enforce policies across accounts.
  - Simplifies account provisioning.

### SCP Hierarchy
- SCPs are applied hierarchically:
  1. Root of the organization.
  2. Organizational Unit (OU).
  3. Individual accounts.
- Policies at higher levels override or constrain lower levels.

### SCP Examples: Blocklist and Allowlist Strategies
- **Blocklist Strategy:** Deny specific actions (e.g., `Deny: "ec2:TerminateInstances"`).
- **Allowlist Strategy:** Explicitly allow only required actions (e.g., `Allow: "s3:*"`).

---

## IAM Conditions
- Define context-based access controls using conditional keys.
- Examples:
  - Restrict access based on IP address: `aws:SourceIp`.
  - Time-based conditions: `aws:CurrentTime`.
  - Specific VPC or subnet: `aws:VpcId`.

---

## IAM for S3
- Use IAM policies to manage access to S3 buckets and objects.
- Combine bucket policies, IAM policies, and ACLs for granular control.

### Resource Policies & `aws:PrincipalOrgID`
- Use resource-based policies with the `aws:PrincipalOrgID` condition to restrict access to resources within your AWS Organization.

---

## IAM Roles vs. Resource-Based Policies
- **IAM Roles:**
  - Temporary credentials to assume a specific identity.
  - Useful for cross-account or service-level access.

- **Resource-Based Policies:**
  - Attached directly to resources like S3, Lambda, or KMS.
  - Supports granting cross-account access without assuming roles.

---

## Amazon EventBridge – Security
- Supports fine-grained IAM permissions for event buses, rules, and targets.
- Use resource-based policies to control cross-account access to event buses.

---

## IAM Permission Boundaries
- Define the maximum permissions a user or role can have.
- Restricts the effective permissions, even if more permissive policies exist.
- Use cases: Delegated administration, enforcing organizational limits.

---

## IAM Policy Evaluation Logic
- Policies are evaluated in the following order:
  1. Explicit **Deny**: Overrides all.
  2. Explicit **Allow**: Grants access.
  3. Implicit **Deny**: Default if no explicit allow is found.

### Example IAM Policy
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::example-bucket"
    },
    {
      "Effect": "Deny",
      "Action": "s3:DeleteObject",
      "Resource": "arn:aws:s3:::example-bucket/*"
    }
  ]
}
```

---

## AWS IAM Identity Center (formerly AWS SSO)
- Centralized service to manage access to AWS accounts and applications.

### AWS IAM Identity Center – Login Flow
- Users log in through a web portal.
- Temporary credentials are issued for AWS Management Console or CLI.

### AWS IAM Identity Center – Fine-grained Permissions and Assignments
- Assign specific permissions to users or groups for individual accounts and applications.

---

## What is Microsoft Active Directory (AD)?
- Centralized directory service for managing user authentication and authorization.
- Supports group policies and single sign-on (SSO).

### AWS Directory Services
- Managed Microsoft AD.
- Integrates with AWS services like EC2 and RDS.

### IAM Identity Center – Active Directory Setup
- Configure IAM Identity Center to use AD for authentication.
- Sync users and groups from AD to AWS accounts.

---

## AWS Control Tower
- Simplifies multi-account setup and governance.
- Provides pre-configured blueprints and automated account provisioning.

### AWS Control Tower – Guardrails
- Preventive and detective policies to ensure compliance.
- Examples:
  - Prevent turning off CloudTrail.
  - Detect and report unencrypted S3 buckets.

---
