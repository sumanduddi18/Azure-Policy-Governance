# Azure Policy & Governance - Interview Preparation

Interview preparation based on the hands-on Azure Policy & Governance Lab.

## Core Topics

- Azure Management Groups
- Azure Policy
- Policy Definitions
- Policy Assignments
- Policy Initiatives
- Policy Compliance
- Policy Remediation
- Azure RBAC
- Resource Tags
- Resource Locks
- Azure Monitor
- Activity Logs
- Log Analytics
- Diagnostic Settings
- Cost Management
- Azure Landing Zone Governance

## Theory Questions

### 1. What is Azure Management Group?

Azure Management Groups are containers used to organize multiple Azure subscriptions and apply governance controls consistently across those subscriptions.

### 2. Why are Management Groups used?

They provide a centralized scope for:

- Azure Policy
- RBAC
- Compliance
- Governance
- Subscription organization

### 3. What is the Azure hierarchy?

Tenant → Management Group → Subscription → Resource Group → Resource

### 4. What is Azure Policy?

Azure Policy is an Azure governance service used to enforce organizational standards, evaluate resource compliance and prevent or audit non-compliant configurations.

### 5. What is the difference between Policy Definition and Policy Assignment?

A Policy Definition contains the governance rule.

A Policy Assignment applies that rule to a specific scope such as a Management Group, Subscription, Resource Group or Resource.

### 6. What is a Policy Initiative?

A Policy Initiative is a collection of related policy definitions grouped together and assigned as a single governance unit.

### 7. What are common Azure Policy effects?

- Audit
- Deny
- Modify
- Append
- DeployIfNotExists
- AuditIfNotExists
- Disabled

### 8. What is the difference between Audit and Deny?

Audit allows the resource but reports it as non-compliant.

Deny prevents the non-compliant resource deployment or update.

### 9. What is Azure RBAC?

Azure RBAC controls who can access Azure resources, what actions they can perform and at which scope.

### 10. Azure Policy vs RBAC?

Azure Policy controls resource configuration and compliance.

Azure RBAC controls user and workload permissions.

Policy answers:

"What configuration is allowed?"

RBAC answers:

"Who can perform this action?"

### 11. What are Azure Resource Tags?

Tags are key-value pairs used to identify and organize resources.

Examples:

Environment = Development

Owner = Suman Duddi

Project = Secure-Landing-Zone

CostCenter = IT-001

### 12. How can mandatory tags be enforced?

Azure Policy can be used to audit, deny or modify resources that do not contain required tags.

### 13. What are Resource Locks?

Resource Locks protect Azure resources from accidental deletion or modification.

Main types:

- CanNotDelete
- ReadOnly

### 14. What is Azure Activity Log?

Activity Log records management-plane operations performed against Azure resources at the subscription level.

Examples include:

- Resource creation
- Resource deletion
- RBAC changes
- Policy changes
- Resource Group changes

### 15. What is Log Analytics?

Log Analytics provides centralized log collection and analysis and supports querying through KQL.

### 16. What are Diagnostic Settings?

Diagnostic Settings define which logs and metrics are collected and where they are sent.

Destinations can include:

- Log Analytics
- Storage Account
- Event Hub

### 17. What is Azure Cost Management?

Azure Cost Management provides visibility into Azure spending through:

- Cost Analysis
- Cost Forecasting
- Budgets
- Cost Alerts
- Resource-level cost analysis

## Scenario-Based Questions

### Scenario 1 - Mandatory Tags

A company requires every production resource to have Environment, Owner and CostCenter tags. Developers are deploying resources without tags. What would you do?

Answer:

I would create an Azure Policy that evaluates the required tags and assign it at the appropriate Management Group, Subscription or Resource Group scope.

I could use Audit to identify existing non-compliant resources, Deny to prevent new non-compliant deployments, or Modify to automatically add or update tags where appropriate.

### Scenario 2 - Restrict Azure Regions

The company only allows resources in approved Azure regions. A developer attempts to deploy a resource in another region.

Answer:

I would assign an Azure Policy that restricts allowed locations and use the Deny effect to prevent deployments outside the approved regions.

### Scenario 3 - Existing Non-Compliant Resources

A policy requiring tags has been assigned, but existing resources are missing the required tags.

Answer:

I would review Policy Compliance to identify non-compliant resources.

If the policy supports remediation, I would create a remediation task to bring existing resources into compliance.

### Scenario 4 - Policy Blocks Deployment

A production deployment fails because Azure Policy returns a Deny result.

Answer:

I would:

1. Review the deployment error.
2. Identify the policy assignment causing the denial.
3. Review the policy definition and parameters.
4. Compare the deployment configuration with the policy requirement.
5. Correct the configuration if it is non-compliant.
6. If it is a legitimate exception, follow the organization's policy exemption process.
7. Re-run the deployment.
8. Verify compliance.

### Scenario 5 - Production Resource Protection

A production Log Analytics Workspace must not be accidentally deleted.

Answer:

I would apply a CanNotDelete Resource Lock to protect the resource from accidental deletion while still allowing authorized configuration changes.

### Scenario 6 - Centralized Governance

An organization has multiple Azure subscriptions and wants the same security policies applied across all of them.

Answer:

I would organize the subscriptions under appropriate Management Groups and assign common Azure Policies at the Management Group scope.

This allows policies to be inherited by child subscriptions.

### Scenario 7 - Policy Exception

A development team needs an exception to an existing policy.

Answer:

I would not disable the policy globally.

I would evaluate the business requirement and use a controlled Policy Exemption with appropriate approval, scope, justification and expiration where applicable.

### Scenario 8 - Governance Monitoring

Security wants to know who changed an Azure Policy assignment.

Answer:

I would check Azure Activity Log for the relevant policy operation and review:

- Caller
- Operation
- Timestamp
- Subscription
- Resource
- Operation status

For centralized monitoring, Activity Logs can be sent to Log Analytics using Diagnostic Settings.

## Production Troubleshooting

### Challenge 1 - Policy Not Working

A policy is assigned but resources are still being deployed with non-compliant configurations.

Check:

- Policy assignment scope
- Policy parameters
- Policy effect
- Policy mode
- Resource type
- Policy exemptions
- Compliance evaluation
- Assignment status

### Challenge 2 - Compliance Suddenly Drops

If compliance decreases unexpectedly:

1. Review Policy Compliance.
2. Identify affected policies.
3. Identify affected resources.
4. Review recent deployments.
5. Check Activity Logs.
6. Check whether policy assignments or parameters changed.
7. Review remediation tasks.
8. Correct the root cause.
9. Revalidate compliance.

### Challenge 3 - Developer Reports Policy Issue

If a developer reports that Azure Policy is blocking a legitimate deployment:

1. Identify the policy.
2. Review the policy rule.
3. Validate the business requirement.
4. Confirm whether the deployment is actually non-compliant.
5. Correct the configuration if possible.
6. Use a Policy Exemption only when justified.
7. Document the exception.

## Project-Specific Questions

### 1. Explain your Azure Policy & Governance project.

Answer:

I implemented an enterprise-style Azure governance lab focused on Management Groups, Azure Policy, RBAC, resource tagging, Resource Locks, monitoring and cost governance.

I created a structured Management Group hierarchy, organized the subscription under the appropriate governance scope, implemented policy controls and validated compliance.

I also implemented resource tagging, reviewed RBAC assignments, configured monitoring and Activity Logs, validated Resource Locks and reviewed Azure Cost Management.

### 2. Why did you use Management Groups?

Answer:

Management Groups provide a centralized governance scope above subscriptions. They allow common policies and RBAC controls to be applied consistently across multiple subscriptions.

### 3. What policies did you implement?

Answer:

I worked with governance scenarios including allowed locations, resource configuration, VM SKU restrictions, required tags, tag inheritance, compliance auditing and policy-based deployment restrictions.

### 4. How did you validate your policies?

Answer:

I reviewed Policy Assignments and Policy Compliance and validated the behavior through Azure Portal configuration and resource deployment testing.

I also reviewed Activity Logs to validate related governance operations.

### 5. Why did you implement Resource Tags?

Answer:

Tags provide metadata for ownership, environment classification, project identification and cost allocation.

They also help with resource organization and governance reporting.

### 6. Why did you use Resource Locks?

Answer:

Resource Locks provide an additional protection layer for critical resources and help prevent accidental deletion or modification.

### 7. Why did you configure Log Analytics?

Answer:

I configured Log Analytics to provide centralized log collection and analysis. It can be used with KQL to investigate Azure activity and support monitoring and troubleshooting.

### 8. How does this project demonstrate Azure Security?

Answer:

The project demonstrates both preventive and detective governance controls.

Preventive controls include Azure Policy, RBAC, Resource Locks and governance standards.

Detective controls include Policy Compliance, Activity Logs, Azure Monitor and Log Analytics.

## Quick Interview Cheat Sheet

| Topic | Key Point |
|---|---|
| Management Group | Organizes subscriptions |
| Azure Policy | Governance and compliance |
| Policy Definition | Defines the rule |
| Policy Assignment | Applies the rule |
| Initiative | Collection of policies |
| Compliance | Policy evaluation result |
| Remediation | Corrects existing non-compliant resources |
| RBAC | Controls who can perform actions |
| Tags | Resource metadata and cost allocation |
| Resource Lock | Protects resources |
| Activity Log | Management-plane events |
| Azure Monitor | Monitoring and observability |
| Log Analytics | Centralized logs and KQL |
| Diagnostic Settings | Routes logs and metrics |
| Cost Management | Cost visibility and optimization |

## Interview Answer Framework

For Azure governance scenarios:

1. Identify the requirement.
2. Identify the affected scope.
3. Select the appropriate Azure governance control.
4. Configure the control.
5. Validate the result.
6. Monitor compliance.
7. Remediate if required.
8. Document exceptions.

For production troubleshooting:

Identify → Investigate → Validate → Remediate → Monitor → Document

## Project Status

Completed

Hands-on Azure Policy and Governance implementation, validation, documentation and interview preparation completed using Microsoft Azure.
