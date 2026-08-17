# Hybrid Identity Lab

Hands-on Identity and Access Management (IAM) lab environment developed to build practical experience with **Microsoft Entra ID, Active Directory, access control, identity lifecycle management, and security administration** while preparing for the **Microsoft SC-300: Identity and Access Administrator** certification.

This repository documents practical IAM scenarios designed to simulate identity administration and security tasks commonly performed in enterprise environments.

---

## Lab Objectives

Key areas of focus include:

- Microsoft Entra ID administration
- Role-Based Access Control (RBAC)
- Least privilege and delegated administration
- Security group management
- Group-based access control
- Identity lifecycle management
- Joiner, Mover, and Leaver (JML) processes
- Account provisioning and deprovisioning
- Session revocation
- Access validation
- Microsoft Entra audit log analysis
- Hybrid identity concepts

---

## Completed Labs

### 03 - Role-Based Access Control (RBAC)

Implemented delegated administrative access in Microsoft Entra ID and validated the permissions available to a limited administrator.

**Concepts demonstrated:**

- Microsoft Entra administrative roles
- Delegated administration
- Least privilege
- Role assignment
- Permission validation
- Privileged-account protection

---

### 04 - Group-Based Access Control

Implemented security-group-based access management to demonstrate how group membership can be used to centrally manage user access.

**Concepts demonstrated:**

- Microsoft Entra security groups
- Group membership management
- Group-based authorization
- Access assignment
- Access removal
- Access verification

---

### 05 - Identity Lifecycle Management (JML)

Performed a complete **Joiner, Mover, and Leaver** identity lifecycle workflow in Microsoft Entra ID.

The scenario included provisioning access for a new employee, modifying access following a department change, securely offboarding a departing employee, and validating administrative actions through audit logs.

**Concepts demonstrated:**

- Joiner, Mover, and Leaver (JML)
- Identity provisioning and deprovisioning
- Least privilege
- Access removal during role changes
- Security group management
- Account disabling
- Session revocation
- Audit log validation
- Access verification

---

## Identity Lifecycle Approach

The labs follow a security-focused approach to identity administration.

**Joiner**

Provision only the access required for the user's role.

**Mover**

Update identity attributes, remove obsolete permissions, and assign access appropriate to the user's new role.

**Leaver**

Disable the account, revoke existing sessions, remove remaining access, and validate the resulting state.

This approach helps reduce excessive permissions, stale access, and unauthorized authentication while maintaining an auditable identity lifecycle.

---

## Lab Architecture

The environment combines cloud identity administration with an on-premises Active Directory lab.

**Cloud Identity**

- Microsoft Entra ID
- Microsoft Azure
- Microsoft Entra administrative roles
- Microsoft Entra security groups
- Microsoft Entra audit logs

**On-Premises Lab**

- Windows Server
- Active Directory Domain Services (AD DS)
- Windows client systems
- Hyper-V

The environment is being expanded to support additional hybrid identity scenarios.

---

## Security Practices

Screenshots and documentation included in this repository are sanitized before publication.

Sensitive information such as tenant-specific identifiers, account details, domains, IP addresses, and other environment-specific information is removed or redacted before material is added to the public portfolio.

---

## Current Focus

Continuing to expand the lab with additional Microsoft Entra ID and hybrid identity scenarios while developing hands-on skills aligned with **Identity and Access Management (IAM)** and the **Microsoft SC-300** certification.

Planned areas of development include:

- Hybrid identity
- Microsoft Entra Connect
- Authentication methods
- Conditional Access
- Identity governance
- Access reviews
- Privileged identity concepts

---

## Skills Demonstrated

`Microsoft Entra ID` `Active Directory` `IAM` `RBAC` `Least Privilege` `Identity Lifecycle Management` `Joiner-Mover-Leaver` `Security Groups` `Access Control` `Account Provisioning` `Account Deprovisioning` `Audit Logs` `Identity Security` `SC-300`
