<!--
Sync Impact Report
Version change: uninitialized scaffold -> 1.0.0 (initial project constitution)
Modified principles:
- PRINCIPLE_1_NAME -> I. Serverless and Infrastructure as Code
- PRINCIPLE_2_NAME -> II. Least Privilege and Secure Defaults
- PRINCIPLE_3_NAME -> III. Testable Contracts
- PRINCIPLE_4_NAME -> IV. Reliability and Observability
- PRINCIPLE_5_NAME -> V. Simplicity and Compatibility
Added sections: Additional Constraints; Development Workflow
Removed sections: None
Follow-up TODO: Confirm the original ratification date.
-->
# test-speckit-copilot-agent Constitution

## Core Principles

### I. Serverless and Infrastructure as Code
AWS resources and their configuration MUST be defined in version-controlled AWS SAM or
CloudFormation templates. Changes MUST NOT depend on undocumented, console-only configuration.
This keeps deployments reproducible and reviewable.

### II. Least Privilege and Secure Defaults
IAM permissions MUST be limited to the actions and resources each function needs. Secrets MUST
NOT be committed to source or templates. Public access, sensitive-data handling, and weakened
security settings MUST be explicit, justified, and reviewed. Inputs crossing a trust boundary
MUST be validated.

### III. Testable Contracts
Functions and integrations MUST have defined event and response expectations. Changes to
handlers MUST include automated tests for relevant behavior, including invalid input and failure
paths. Changes to infrastructure or service boundaries MUST include validation or integration
tests appropriate to the changed contract.

### IV. Reliability and Observability
Event-driven processing MUST account for retries and duplicate delivery; handlers MUST be
idempotent when repeated processing could cause side effects. Functions MUST have deliberate
timeouts and resource limits. Operationally significant failures MUST be observable through
structured logs and, where appropriate, metrics or alarms. Logs MUST NOT expose secrets or
unnecessary personal data.

### V. Simplicity and Compatibility
The architecture MUST use the simplest design that meets documented requirements. Changes to
public API, event, or persisted-data contracts MUST preserve compatibility or document a
controlled migration. New dependencies and AWS resources MUST have a clear operational purpose.

## Additional Constraints

The application uses AWS SAM to define serverless infrastructure and AWS Lambda-based workloads.
Infrastructure changes MUST follow SAM and CloudFormation resource schemas and keep environment-
specific values in parameters or configuration rather than duplicating templates. Resource
permissions, retention, encryption, and network exposure MUST be explicitly reviewed for each
resource where applicable.

## Development Workflow

Every change MUST be reviewed for compliance with these principles. Before merging, contributors
MUST run the repository's available template validation and relevant automated tests, and MUST
resolve failures caused by the change. Changes affecting AWS integrations MUST be validated with
tests or checks that exercise the affected boundary. Deployment changes MUST be made through the
declared infrastructure-as-code workflow; production deployment MUST follow the project's
authorized release process.

## Governance

This constitution governs project decisions and supersedes conflicting informal practices.
Amendments MUST be proposed through a reviewed change to this file. The change MUST explain its
reason, assess effects on existing principles and workflows, and update the version and amendment
date. Reviewers MUST check the proposed change for consistency with the principles and identify
any required migration or follow-up work.

Versioning follows semantic versioning: MAJOR for incompatible removals or redefinitions of
governance, MINOR for new or materially expanded principles or sections, and PATCH for
non-semantic clarifications and corrections. Compliance MUST be considered during implementation
planning and code review; deviations MUST be explicitly justified and approved in review.

**Version**: 1.0.0 | **Ratified**: TODO(RATIFICATION_DATE) | **Last Amended**: 2026-10-16
