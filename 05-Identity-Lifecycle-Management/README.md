# Identity Lifecycle Management – Joiner, Mover, Leaver (JML)

## Overview

This lab demonstrates a hands-on Identity Lifecycle Management workflow in Microsoft Entra ID using the **Joiner, Mover, and Leaver (JML)** model.

The objective was to simulate common identity administration tasks performed during an employee's lifecycle, including:

- Provisioning access for a new employee
- Modifying access when an employee changes departments
- Removing obsolete access following a role change
- Disabling an account during offboarding
- Revoking active sign-in sessions
- Removing remaining group-based access
- Validating identity changes through Microsoft Entra audit logs

The lab emphasizes **least privilege, access lifecycle management, verification, and auditability**.

---

## Lab Environment

- Microsoft Entra ID
- Microsoft Azure Portal
- Security Groups
- Microsoft Entra Audit Logs
- Dedicated administrative account
- Test users representing employee lifecycle scenarios

---

# 1. Joiner Scenario

## Scenario

A new employee requires access to resources associated with the **Sales department**.

As part of the Joiner process, the user account was reviewed and access was provisioned through membership in the appropriate Microsoft Entra security group.

## Assign Sales Access

The new employee was assigned to the `SG-Sales` security group.

![Joiner - Assign Sales Group](05-LIFECYCLE-01-Joiner-Assign-Sales-Group.png)

## Review New User

The newly provisioned Sales user was reviewed in Microsoft Entra ID.

![Joiner - New Sales User Review](05-LIFECYCLE-01-New-Sales-User-Review.png)

## Verify Access

Group membership was verified to confirm that the required Sales access had been successfully provisioned.

![Joiner - Sales User Verified](05-LIFECYCLE-02-New-Sales-User-Verified.png)

### Joiner Result

The employee received the appropriate group-based access required for the Sales role.

This demonstrates the principle of assigning access based on **business requirements and job function** rather than granting unnecessary permissions directly to individual users.

---

# 2. Mover Scenario

## Scenario

An existing employee moved from the **Sales department to the Finance department**.

A role change requires more than simply granting new access. Existing permissions must also be reviewed and removed when they are no longer required.

This prevents **access accumulation** and helps enforce the principle of least privilege.

## Review Existing Sales Access

Before making changes, the employee's existing `SG-Sales` membership was documented.

![Mover - Existing Sales Membership](05-LIFECYCLE-03-Mover-PreChange-Sales-Membership.png)

## Update Identity Attributes

The employee's identity information was updated to reflect the new organizational role.

![Mover - Identity Attributes Updated](05-LIFECYCLE-04-Mover-Identity-Attributes-Updated.png)

## Remove Previous Sales Access

Because Sales access was no longer required, the employee was removed from `SG-Sales`.

![Mover - Remove Sales Access](05-LIFECYCLE-05-Mover-Remove-Sales-Access.png)

The removal was then verified.

![Mover - Verify Sales Access Removed](05-LIFECYCLE-06-Mover-Verify-Sales-Access-Removed.png)

## Assign Finance Access

The employee was added to the `SG-Finance` security group to provide access appropriate to the new role.

![Mover - Add Finance Access](05-LIFECYCLE-07-Mover-Add-Finance-Access.png)

The new Finance access was then verified.

![Mover - Verify Finance Access](05-LIFECYCLE-08-Mover-Verify-Finance-Access.png)

### Mover Result

The employee transitioned from Sales access to Finance access while obsolete permissions were removed.

The final access state reflected the employee's new business role rather than retaining permissions from both departments.

This demonstrates:

- Least privilege
- Role-based access changes
- Prevention of permission accumulation
- Access verification following identity changes

---

# 3. Leaver Scenario

## Scenario

An employee is leaving the organization and must be securely offboarded.

The objective of the Leaver process was to prevent further authentication while also removing remaining group-based access and producing evidence that the changes occurred.

## Review Account Before Offboarding

The employee's account state was reviewed before beginning the offboarding process.

![Leaver - Before Offboarding](05-LIFECYCLE-09-Leaver-Before-Offboarding.png)

## Disable the User Account

The account was disabled to prevent future authentication.

![Leaver - Disable Account](05-LIFECYCLE-10-Leaver-Disable-Account.png)

The account status was then reviewed to confirm that the account was disabled.

![Leaver - Verify Account Disabled](05-LIFECYCLE-11-Leaver-Verify-Account-Disabled.png)

---

# 4. Revoke Existing Sessions

Disabling an account prevents future authentication, but an offboarding process should also address existing authenticated sessions.

The user's active sign-in sessions were revoked.

![Leaver - Revoke All Sessions](05-LIFECYCLE-12-Leaver-Revoke-All-Sessions.png)

The operation was then verified.

![Leaver - Verify Sessions Revoked](05-LIFECYCLE-13-Leaver-Verify-Sessions-Revoked.png)

This step helps reduce the risk of previously issued authentication sessions remaining usable after the employee has been offboarded.

---

# 5. Remove Remaining Access

After disabling the account and revoking sessions, the user's remaining group memberships were reviewed.

The employee still had Finance group access.

![Leaver - Existing Group Access](05-LIFECYCLE-14-Leaver-Existing-Group-Access.png)

The employee was removed from `SG-Finance`.

![Leaver - Remove Finance Access](05-LIFECYCLE-15-Leaver-Remove-Finance-Access.png)

The group membership state was then verified to confirm that the access had been removed.

![Leaver - Verify Group Access Removed](05-LIFECYCLE-16-Leaver-Verify-Group-Access-Removed.png)

---

# 6. Audit Log Validation

Administrative actions should be verifiable and auditable.

Microsoft Entra audit logs were reviewed following the offboarding actions.

![Leaver - Audit Log Evidence](05-LIFECYCLE-17-Leaver-Audit-Log-Evidence.png)

## Disable Account Audit Event

The detailed audit event confirmed that the **Disable account** operation completed successfully.

![Leaver - Disable Account Audit Details](05-LIFECYCLE-18-Leaver-Audit-Disable-Account-Details.png)

## Validate AccountEnabled Change

The modified properties associated with the audit event were reviewed.

The audit record showed:

- **Property:** `AccountEnabled`
- **Old Value:** `true`
- **New Value:** `false`

![Leaver - AccountEnabled True to False](05-LIFECYCLE-19-Leaver-Audit-AccountEnabled-True-to-False.png)

This provides direct audit evidence that the identity transitioned from an enabled state to a disabled state.

---

# 7. Final Access Verification

A final review of the user was performed after the offboarding actions were completed.

![Leaver - Final Access Verification](05-LIFECYCLE-20-Leaver-Final-Access-Verification.png)

The final state confirmed that:

- The account was disabled
- Group memberships had been removed
- Existing sessions had been revoked
- The account disable operation was recorded in the audit logs

---

# Security Concepts Demonstrated

This lab provided hands-on experience with several core Identity and Access Management concepts:

### Identity Lifecycle Management

Managing identities through the Joiner, Mover, and Leaver stages of the employee lifecycle.

### Least Privilege

Users should retain only the access required for their current job responsibilities.

### Group-Based Access Control

Security groups were used to manage departmental access rather than relying on individual permission assignments.

### Access Removal During Role Changes

The Mover workflow demonstrated that changing departments requires both **granting new access and removing obsolete access**.

### Secure Offboarding

The Leaver workflow demonstrated multiple layers of account deprovisioning:

1. Disable the identity
2. Revoke existing authentication sessions
3. Remove remaining group memberships
4. Verify the resulting access state
5. Review audit evidence

### Auditability

Microsoft Entra audit logs were used to validate administrative actions and confirm changes to identity properties.

---

# Key Takeaways

The most important lesson from this lab is that Identity Lifecycle Management is not simply about creating and deleting accounts.

Effective lifecycle management requires continuously aligning a user's access with their current relationship to the organization.

A Joiner needs the correct access to perform their job.

A Mover requires new access while obsolete permissions must be removed.

A Leaver requires prompt account restriction, session revocation, access removal, and verification.

Together, these controls help reduce excessive permissions, stale access, unauthorized authentication, and other identity-related security risks.

---

## Skills Demonstrated

`Microsoft Entra ID` `Identity Lifecycle Management` `Joiner-Mover-Leaver` `IAM` `Security Groups` `Least Privilege` `Access Control` `Account Provisioning` `Account Deprovisioning` `Session Revocation` `Audit Logs` `Access Validation`
