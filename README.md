# BINCOM-INTERNSHIP-ACADEMY-5TH-ASSIGNMENT
Authorized AWS IAM security assessment demonstrating a controlled privilege-escalation path, Administrator-Access attachment, least-privilege remediation, and post-remediation verification using AWS CLI.
I completed my BINCOM Academy 5th Contact Assignment, focusing on an authorized AWS IAM privilege-escalation assessment.

Project: AWS IAM Privilege Escalation Assessment

Author: Oyewumi Yusuf Olayemi
Role: BINCOM Academy Intern
Period: September 2026

The assessment simulated a realistic IAM authorization weakness in a controlled AWS laboratory environment.

A dedicated IAM identity was intentionally granted iam:AttachUserPolicy. I then demonstrated how that permission could be abused to attach the AWS-managed AdministratorAccess policy to the same identity.

The escalation was not treated as complete until it was independently verified through AWS CLI.

Attack chain

Misconfigured IAM identity
        ↓
iam:AttachUserPolicy
        ↓
Attach AdministratorAccess
        ↓
AdministratorAccess confirmed

Remediation

The vulnerable configuration was then remediated using the Principle of Least Privilege:

AdministratorAccess removed
        ↓
Vulnerable inline policy removed
        ↓
Permissions policies = 0
        ↓
Same escalation command repeated
        ↓
AccessDenied

The post-remediation test therefore demonstrates that the escalation path was actually eliminated rather than merely assumed to be fixed.

Evidence

The project contains a chronological evidence chain from E01 to E13, covering:

AWS CLI baseline

IAM baseline

Dedicated test-user creation

Vulnerable policy introduction

Escalation attempt

AdministratorAccess verification

Remediation

Least-privilege state

Post-remediation AccessDenied

Final IAM verification

Security lesson

The main lesson from the project is that permissions-management actions require particular scrutiny. A principal that can attach managed policies may be able to change the effective authorization of IAM identities if that capability is not tightly constrained.

AWS's current IAM guidance recommends least privilege, policy validation with IAM Access Analyzer, regular review/removal of unused permissions, and restrictions around permissions-management actions.

Disclaimer

This project was performed strictly as an authorized laboratory assessment for BINCOM Academy. It is an educational security assessment and is not a public vulnerability disclosure or a CVE claim.

Project ID: BINCOM-IAM-001
