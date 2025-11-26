# Runbook

Operational guide for deploying, operating, and maintaining the **APM Distributed Profiling** platform.

## 1. Deployment

### Prerequisites

- AWS CLI configured with appropriate credentials
- Node.js 18+ and npm installed
- AWS CDK CLI installed (`npm install -g aws-cdk`)

### Deploy Steps

```bash
# Install dependencies
npm install

# Bootstrap CDK (first time only)
cdk bootstrap

# Deploy to dev
cdk deploy --context environment=dev

# Deploy to production
cdk deploy --context environment=prod
```

## 2. Agent Setup

### Application Integration

```java
// Java example - add to JVM arguments
-javaagent:/path/to/codeguru-profiler-agent.jar
```

```python
# Python example
from codeguru_profiler_agent import Profiler
Profiler(profiling_group_name='my-app').start()
```

## 3. Monitoring

### Key Metrics to Watch

- **Profile submission rate**: Agent health indicator
- **Flame graph generation time**: Processing latency
- **Anomaly detection alerts**: Performance regressions
- **Agent coverage**: Percentage of services instrumented

### Dashboards

Pre-configured dashboards show:

- Service performance overview
- CPU hotspot analysis
- Memory allocation patterns
- Regression detection alerts

## 4. Maintenance

### Regular Tasks

- Review profiling group configurations quarterly
- Update profiling agents to latest version
- Archive old profiles to reduce storage costs
- Review and tune anomaly detection thresholds

### Troubleshooting Agent Issues

```bash
# Check agent logs
tail -f /var/log/codeguru-profiler/profiler.log

# Verify IAM permissions
aws iam simulate-principal-policy --policy-source-arn <agent-role-arn>
```

### Teardown

```bash
cdk destroy --context environment=dev
```

> For troubleshooting common issues, see `docs/troubleshooting.md`.
