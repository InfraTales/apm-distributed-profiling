# Cost Analysis (₹)

This document provides cost estimates for the **APM Distributed Profiling** architecture in **Indian Rupees (₹)**.

## Production Environment

At production scale (continuous profiling across services), the architecture typically costs:

| Service | Monthly Cost (₹) | Notes |
|---------|------------------|-------|
| **CodeGuru Profiler** | ₹20,000–35,000 | Per profiling group |
| **X-Ray** | ₹8,000–15,000 | Distributed tracing |
| **CloudWatch** | ₹10,000–18,000 | Metrics and dashboards |
| **Lambda (processors)** | ₹5,000–10,000 | Profile aggregation |
| **S3 (profiles)** | ₹3,000–5,000 | Profile storage |
| **SNS/EventBridge** | ₹1,000–2,000 | Alerting |
| **Total** | **₹50,000–85,000** | ~$625–1,060/month |

## Development Environment

For dev/staging environments:

| Environment | Approx Monthly Cost (₹) | Notes |
|------------|--------------------------|-------|
| Dev | ₹10,000–15,000 | Single profiling group, reduced sampling |
| Staging | ₹20,000–35,000 | Multiple groups, moderate sampling |
| Production | ₹50,000–85,000 | Full coverage, continuous profiling |

## Cost Optimization Strategies

- **Sampling rates** – Reduce profiling frequency for stable services
- **Targeted profiling** – Focus on critical paths and hot services
- **Retention policies** – Archive older profiles to S3 Glacier
- **Reserved capacity** – Use savings plans for predictable Lambda usage
- **Aggregate metrics** – Pre-compute common flame graph aggregations

## Related Documentation

See `ARCHITECTURE.md` for service details and `DEPLOYMENT.md` for configuration options.
