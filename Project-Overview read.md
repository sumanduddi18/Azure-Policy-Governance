# Project 4 – Azure Policy & Governance

## Enterprise Azure Governance & Landing Zone Implementation

## Project Overview

This project demonstrates the design and implementation of an enterprise-style Azure governance framework using Microsoft Azure Management Groups, Azure Policy, Role-Based Access Control (RBAC), resource organization, tagging, monitoring, and cost governance.

The environment follows Azure Landing Zone governance principles to establish a structured, secure, and manageable Azure environment.

The objective was to simulate how an enterprise organizes subscriptions, applies governance controls, manages access, standardizes resources, enables monitoring, and maintains cost visibility across Azure environments.

---

## Business Objective

Organizations operating Azure at scale require centralized governance to maintain:

- Security and compliance
- Standardized resource deployment
- Controlled administrative access
- Resource organization
- Cost visibility and accountability
- Centralized monitoring
- Consistent operational standards

This project addresses these requirements by implementing governance controls across the Azure hierarchy.

---

## Architecture Approach

The governance hierarchy was designed using Management Groups and subscription organization.

### Management Group Hierarchy

Tenant Root Group
│
└── landing-zones
    │
    ├── Development
    │   └── Learning-labs Subscription
    │
    ├── Production
    │
    └── Platform
        ├── Connectivity
        ├── Identity
        └── Management

Additional sandbox governance structure was also established.

---

## Governance Components

### 1. Management Groups

Implemented a hierarchical Management Group structure to provide centralized governance and policy scope.

Structure includes:

- Tenant Root Group
- Landing Zones
- Development
- Production
- Platform
- Connectivity
- Identity
- Management
- Sandbox

---

### 2. Subscription Organization

The Azure subscription was placed under the appropriate Development Management Group to demonstrate enterprise subscription governance.

This establishes a scalable hierarchy where governance policies can be inherited from higher scopes.

---

### 3. Azure RBAC

Validated subscription-level Role-Based Access Control assignments.

The environment demonstrates:

- Owner role assignments
- Privileged role assignments
- Service principal permissions
- Managed identity permissions
- Scope-based access control
- Inherited permissions

The objective is to demonstrate least-privilege access and centralized authorization management.

---

### 4. Resource Group Governance

Resources were organized using workload and platform-oriented Resource Groups.

Example structure:

- `rg-platform-network-dev`
- `rg-platform-identity-dev`
- `rg-platform-management-dev`
- `rg-shared-services-dev`
- `rg-workload-app1-dev`
- `rg-monitoring-dev`

This provides clear separation between platform, shared services, monitoring, and workload resources.

---

### 5. Resource Naming Standard

A consistent naming convention was implemented.

Example:

`<resource-type>-<function>-<environment>`

Examples:

- `rg-platform-network-dev`
- `rg-platform-identity-dev`
- `rg-monitoring-dev`
- `vnet-hub-dev`
- `nsg-web-dev`

This improves operational visibility and simplifies resource management.

---

### 6. Azure Resource Tagging

Resource Groups were tagged using standardized metadata.

Implemented tags include:

| Tag | Example Value |
|---|---|
| Environment | Development |
| Project | Secure-Landing-Zone |
| Owner | Suman Duddi |
| CostCenter | IT-001 |

Tags provide:

- Cost allocation
- Resource ownership
- Environment identification
- Project tracking
- Operational accountability

---

### 7. Azure Monitor & Log Analytics

Implemented centralized monitoring using Azure Monitor and Log Analytics.

A Log Analytics workspace was created:

`law-monitoring-dev`

The workspace was configured in Central India using the Pay-As-You-Go pricing model.

Monitoring capabilities include:

- Activity Logs
- Administrative events
- Resource monitoring
- Centralized log collection
- Operational troubleshooting

---

### 8. Diagnostic Settings

Configured subscription-level diagnostic settings to send Administrative Activity Logs to the Log Analytics workspace.

Configuration:

**Diagnostic Setting:**

`diag-subscription-monitoring`

**Destination:**

`law-monitoring-dev`

**Log Category:**

`Administrative`

This provides centralized visibility into Azure management-plane operations.

---

### 9. Azure Network Watcher

Validated Azure Network Watcher deployment in Central India.

Resource:

`NetworkWatcher_centralindia`

Network Watcher provides network troubleshooting and diagnostic capabilities for Azure networking resources.

---

### 10. Activity Log Validation

Azure Monitor Activity Log was used to validate governance-related operations.

Validated events included:

- Resource group updates
- Deployment validation
- Diagnostic setting creation
- Diagnostic setting deletion
- Policy-related operations
- Network Watcher operations

This demonstrates how administrative activity can be audited and investigated.

---

### 11. Cost Governance

Azure Cost Analysis was reviewed to understand resource consumption and identify major cost contributors.

The project specifically demonstrates the importance of:

- Cost visibility
- Resource-level cost analysis
- Service-level cost analysis
- Forecast monitoring
- Cost optimization

The lab environment was operated using a Pay-As-You-Go Azure subscription.

---

## Governance Scope

The governance model covers the following Azure scopes:

1. Tenant
2. Management Group
3. Subscription
4. Resource Group
5. Resource

This demonstrates Azure's hierarchical governance model and inheritance capabilities.

---

## Key Azure Services

- Azure Management Groups
- Azure Policy
- Azure RBAC
- Microsoft Entra ID
- Azure Resource Groups
- Azure Resource Manager
- Azure Monitor
- Log Analytics
- Activity Log
- Diagnostic Settings
- Network Watcher
- Azure Cost Management
- Azure Advisor
- Azure Landing Zones

---

## Skills Demonstrated

### Azure Governance

- Management Group hierarchy
- Subscription organization
- Azure Policy concepts
- Governance scope
- Resource organization
- Naming standards
- Tagging strategy

### Identity & Access Management

- Azure RBAC
- Role assignments
- Inherited permissions
- Privileged access
- Managed identities
- Service principals
- Scope-based authorization

### Monitoring

- Azure Monitor
- Activity Logs
- Diagnostic Settings
- Log Analytics
- Administrative event monitoring

### Networking

- Network Watcher
- Hub network organization
- NSG organization
- Network resource governance

### Cost Management

- Cost Analysis
- Cost visibility
- Service-level cost analysis
- Forecast analysis
- Cost optimization

---

## Enterprise Design Principles

The implementation follows these governance principles:

- Centralized governance
- Least-privilege access
- Standardized resource naming
- Consistent tagging
- Separation of platform and workload resources
- Centralized monitoring
- Cost accountability
- Scalable management hierarchy
- Policy-driven governance
- Environment separation

---

## Validation

The implementation was validated through Azure Portal configuration and Activity Log evidence.

Validation included:

- Management Group hierarchy
- Subscription placement
- RBAC assignments
- Resource Group structure
- Network resources
- Monitoring resources
- Log Analytics workspace
- Diagnostic Settings
- Activity Logs
- Network Watcher
- Resource tags
- Cost Analysis

---

## Project Outcome

Successfully implemented and validated an enterprise-style Azure governance framework based on Azure Landing Zone principles.

The project demonstrates practical understanding of how Azure environments can be structured and governed at scale while maintaining:

- Security
- Compliance
- Operational visibility
- Access control
- Standardization
- Cost management
- Scalability

---

## Interview Focus

This project provides practical discussion points for Azure Cloud Engineer, Azure Administrator, Azure Security Engineer, Cloud Security Engineer, and Azure Governance roles.

Key interview areas include:

- Management Groups vs Subscriptions vs Resource Groups
- Azure Policy vs RBAC
- Policy inheritance
- Azure Landing Zones
- Governance hierarchy
- Tagging strategy
- Enterprise naming conventions
- Least-privilege access
- Diagnostic Settings
- Activity Logs
- Log Analytics
- Cost governance
- Network Watcher
- Enterprise Azure governance scenarios
