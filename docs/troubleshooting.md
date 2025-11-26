# Troubleshooting

Common issues and resolutions for the **APM Distributed Profiling** platform.

## Agent Issues

### 1. Profiling Agent Not Submitting Data

**Symptom:** No profiles appearing in CodeGuru console.

**Resolution:**
- Verify IAM role has `codeguru-profiler:*` permissions
- Check network connectivity to CodeGuru endpoint
- Review agent logs for authentication errors
- Ensure profiling group exists in the target region

### 2. High Agent Overhead

**Symptom:** Application performance degraded after enabling profiling.

**Resolution:**
- Reduce sampling rate in agent configuration
- Exclude low-value code paths from profiling
- Use heap profiling only when needed (CPU-only by default)

## Data Quality Issues

### 3. Incomplete Flame Graphs

**Symptom:** Flame graphs missing expected methods or showing gaps.

**Resolution:**
- Verify application has debug symbols enabled
- Check agent version compatibility with runtime
- Ensure sufficient profiling duration (minimum 5 minutes)

### 4. False Positive Anomalies

**Symptom:** Too many regression alerts for normal variations.

**Resolution:**
- Increase anomaly detection threshold
- Extend baseline period for seasonal patterns
- Exclude known variable operations from detection

## Performance Issues

### 5. Slow Dashboard Loading

**Symptom:** Flame graphs take too long to render.

**Resolution:**
- Reduce time range for initial queries
- Pre-aggregate profiles for common views
- Check browser memory (large profiles need RAM)

### 6. Missing Cross-Service Traces

**Symptom:** Distributed traces don't connect across services.

**Resolution:**
- Verify X-Ray SDK is properly propagating trace headers
- Check all services are in the same sampling group
- Review service mesh / API gateway header forwarding

## Cost Issues

### 7. Unexpected High Costs

**Symptom:** Monthly bill higher than estimates.

**Resolution:**
- Review profiling group count – consolidate where possible
- Reduce sampling rate for high-traffic services
- Implement lifecycle policies for profile storage

> For architecture details, see `ARCHITECTURE.md`.
