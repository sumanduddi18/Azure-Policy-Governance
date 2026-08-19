# Azure Policy & Governance — Interview Preparation

Interview preparation guide based on the hands-on Azure Policy & Governance Lab.

This section covers theoretical concepts, scenario-based questions, production challenges and project-specific interview questions.

---

# 1. Core Concepts

## Azure Governance

Azure Governance is the collection of mechanisms used to control, standardize, secure and manage Azure resources across an organization.

Key governance capabilities include:

- Management Groups
- Azure Policy
- Azure RBAC
- Resource Locks
- Resource Tags
- Resource Naming Standards
- Azure Resource Manager
- Azure Monitor
- Azure Activity Logs
- Cost Management

---

# 2. Management Groups

Azure Management Groups provide a hierarchy above subscriptions.

A typical enterprise hierarchy can be:

```text
Tenant Root Group
│
└── Landing Zones
    │
    ├── Platform
    │   ├── Connectivity
    │   ├── Identity
    │   └── Management
    │
    └── Development
        │
        └── Azure Subscription
