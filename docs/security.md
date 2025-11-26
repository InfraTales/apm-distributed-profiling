# Security Overview

This document summarizes the security posture of the **APM Distributed Profiling** architecture.

## Defense-in-Depth

The system applies multiple layers of security controls:

### Identity & Access (IAM)

- Least-privilege IAM roles for profiling agents
- Separate roles for data collection, processing, and querying
- Cross-account access controls for multi-account setups

### Data Protection

- **Profile data encryption**: KMS encryption for stored profiles
- **Transit encryption**: TLS 1.2+ for all agent-to-service communication
- **Data sanitization**: Scrubbing of sensitive data from stack traces

### Network Isolation

- VPC endpoints for CodeGuru and X-Ray access
- Private subnet deployment for processing components
- Security groups limiting egress to required AWS services

### Access Controls

- IAM-based access to profiling dashboards
- Resource-based policies for cross-account scenarios
- Audit logging via CloudTrail

## Sensitive Data Handling

Profiling data may contain:

- Method names and parameters
- Stack traces with variable names
- Memory allocation patterns

Ensure PII/sensitive data is not passed as method arguments or use data masking.

## Compliance Considerations

The architecture supports:

- SOC 2 Type II controls
- Internal security audits
- Performance data governance policies

> For detailed security configurations, see `SECURITY.md` in the project root.
