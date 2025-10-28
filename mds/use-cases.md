# Use Cases & Examples

See how builders are using The HorizonSec Project to secure their applications across different scenarios, tech stacks, and team sizes.

---

## Common Use Cases

### 1. 🚀 **Pre-Commit Security Checks**

**Scenario**: Catch security issues before they're committed to version control.

**Solution**: Use ARTEMIS with Git pre-commit hooks

```bash
#!/bin/bash
# .git/hooks/pre-commit

echo "Running security scan..."
artemis scan --quick --staged-only

if [ $? -ne 0 ]; then
    echo "❌ Security issues found. Commit blocked."
    echo "Run 'artemis report' for details or use --no-verify to bypass."
    exit 1
fi

echo "✅ Security scan passed!"
```

**Benefits**:
- Immediate feedback during development
- Prevents vulnerable code from entering codebase
- Educates developers on secure coding practices

**Best For**: Solo developers, small teams, open-source projects

---

### 2. 🔄 **Continuous Security in CI/CD**

**Scenario**: Automatically scan every pull request and deployment.

**Solution**: GitHub Actions workflow

```yaml
name: Security Scan

on:
  pull_request:
    branches: [main, develop]
  push:
    branches: [main]

jobs:
  security:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v3
      
      - name: ARTEMIS Static Analysis
        uses: horizonsec/artemis-action@v1
        with:
          fail-on-severity: high
          
      - name: DEMETER Infrastructure Scan
        uses: horizonsec/demeter-action@v1
        with:
          provider: aws
          
      - name: Comment PR
        uses: horizonsec/comment-action@v1
        if: github.event_name == 'pull_request'
        with:
          include-remediation: true
          
      - name: Upload Results
        uses: github/codeql-action/upload-sarif@v2
        if: always()
        with:
          sarif_file: horizonsec-results.sarif
```

**Benefits**:
- Automated security gates
- PR comments with actionable findings
- No manual security reviews needed for common issues
- Integrates with GitHub Security tab

**Best For**: Teams of any size using CI/CD

---

### 3. 🏗️ **Infrastructure-as-Code Validation**

**Scenario**: Ensure cloud infrastructure is secure before deployment.

**Solution**: DEMETER scanning of Terraform/CloudFormation

```bash
# Scan Terraform before applying
demeter scan terraform/ --output report.html

# Validate specific resources
demeter validate terraform/prod/main.tf

# Check compliance
demeter compliance --framework cis-aws --level 1
```

**Example Finding**:
```
❌ S3 Bucket Not Encrypted
  Resource: aws_s3_bucket.uploads
  File: terraform/storage.tf:12
  Severity: HIGH
  
  Issue: S3 bucket does not have server-side encryption enabled
  
  Recommendation:
  Add encryption configuration to your bucket:
  
  resource "aws_s3_bucket" "uploads" {
    bucket = "my-uploads"
    
    server_side_encryption_configuration {
      rule {
        apply_server_side_encryption_by_default {
          sse_algorithm = "AES256"
        }
      }
    }
  }
  
  References:
  - CIS AWS Benchmark 2.1.1
  - https://docs.aws.amazon.com/s3/encryption
```

**Benefits**:
- Catch misconfigurations before deployment
- Enforce security best practices
- Meet compliance requirements
- Prevent costly production incidents

**Best For**: DevOps teams, platform engineers, SREs

---

### 4. 🔍 **Dependency Vulnerability Management**

**Scenario**: Track and fix vulnerable dependencies in your supply chain.

**Solution**: ARTEMIS dependency scanning

```bash
# Scan dependencies for vulnerabilities
artemis dependencies --check-cve

# Generate SBOM (Software Bill of Materials)
artemis dependencies --sbom --format spdx

# Check license compliance
artemis dependencies --check-licenses --allowed MIT,Apache-2.0
```

**Example Output**:
```
📦 Dependency Vulnerabilities Found

CRITICAL: express 4.16.0
  CVE-2022-24999: Arbitrary code execution via qs parameter
  Fix: Upgrade to express 4.17.3 or higher
  Command: npm update express

HIGH: lodash 4.17.19
  CVE-2020-8203: Prototype pollution vulnerability
  Fix: Upgrade to lodash 4.17.21 or higher
  Command: npm update lodash

Summary:
  2 critical, 1 high, 3 medium vulnerabilities found
  Run 'artemis dependencies --fix' to auto-update
```

**Benefits**:
- Stay ahead of supply chain attacks
- Automated vulnerability discovery
- Easy remediation guidance
- Compliance documentation (SBOM)

**Best For**: All teams (universal concern)

---

### 5. 🛡️ **Runtime Security Monitoring**

**Scenario**: Monitor containerized applications for threats during runtime.

**Solution**: HADES endpoint security

```bash
# Monitor all containers
hades monitor --all

# Monitor specific container
hades monitor --container my-app

# Set security policies
hades policy apply --file security-policy.yml
```

**Example Policy**:
```yaml
# security-policy.yml
version: "1.0"

policies:
  - name: "Block Crypto Mining"
    action: kill
    conditions:
      - process_name_contains: ["xmrig", "cgminer"]
      - cpu_usage_above: 80
      
  - name: "Prevent Privilege Escalation"
    action: alert
    conditions:
      - syscall: ["setuid", "setgid"]
      - user: "!root"
      
  - name: "Network Egress Control"
    action: block
    conditions:
      - destination_port: [4444, 5555, 6666]
      - protocol: "tcp"
```

**Benefits**:
- Real-time threat detection
- Prevent container escapes
- Stop cryptominers and malware
- Audit and forensics

**Best For**: Kubernetes users, container-based deployments

---

### 6. 🎯 **Security Gate in Release Pipeline**

**Scenario**: Block releases with critical security issues.

**Solution**: GAIA orchestration with quality gates

```yaml
# gaia-config.yml
version: "1.0"

gates:
  - name: "Critical Vulnerability Check"
    modules: [artemis, demeter]
    conditions:
      max_critical: 0
      max_high: 3
    actions:
      on_fail: block
      on_pass: continue
      
  - name: "Compliance Validation"
    modules: [demeter]
    conditions:
      compliance_frameworks:
        - name: "CIS-AWS"
          minimum_score: 85
    actions:
      on_fail: block
      
notifications:
  slack:
    webhook: "${SLACK_WEBHOOK}"
    channels: ["#security", "#releases"]
  email:
    recipients: ["security@company.com"]
```

```bash
# Run gate checks before deployment
gaia validate --config gaia-config.yml --stage production

# Result:
# ✅ Critical Vulnerability Check: PASSED (0 critical, 2 high)
# ❌ Compliance Validation: FAILED (CIS-AWS: 82/100)
# 
# Deployment BLOCKED. Fix compliance issues to proceed.
```

**Benefits**:
- Automated go/no-go decisions
- Consistent security standards
- Audit trail for compliance
- Integration with deployment tools

**Best For**: Regulated industries, mature DevOps practices

---

## Industry-Specific Examples

### 🏦 **Financial Services**

**Requirements**:
- PCI-DSS compliance
- Secrets management
- Data encryption
- Access control validation

**HorizonSec Configuration**:
```yaml
# Strict compliance scanning
compliance:
  frameworks:
    - pci-dss-3.2.1
    - sox
  
rules:
  enable:
    - hardcoded-secrets
    - sql-injection
    - xss
    - insecure-crypto
    - weak-authentication
    - sensitive-data-exposure
    
thresholds:
  fail_on: medium  # Stricter than default
  
encryption:
  enforce: true
  minimum_strength: 256
```

---

### 🏥 **Healthcare (HIPAA)**

**Requirements**:
- PHI protection
- Access logging
- Encryption at rest and in transit
- Audit trails

**HorizonSec Configuration**:
```yaml
compliance:
  frameworks:
    - hipaa
    
rules:
  enable:
    - phi-exposure
    - missing-encryption
    - inadequate-logging
    - weak-access-control
    
scanning:
  include_data_flow: true
  track_phi: true
  
reporting:
  include_audit_trail: true
  format: detailed
```

---

### 🛒 **E-commerce**

**Requirements**:
- Payment data security
- Customer data protection
- API security
- Third-party integration security

**HorizonSec Configuration**:
```yaml
focus_areas:
  - payment-processing
  - api-security
  - third-party-integrations
  
rules:
  enable:
    - insecure-payment-flow
    - api-authentication-bypass
    - third-party-data-leak
    - session-fixation
    - csrf
    
dependencies:
  track_third_party: true
  alert_on_cve: true
```

---

## Tech Stack Examples

### Python + Django

```bash
# Comprehensive Python security scan
artemis scan . \
  --language python \
  --framework django \
  --include-tests \
  --check-sql-injection \
  --check-xss \
  --check-csrf

# Django-specific security checks
artemis scan . --profile django-secure
```

**Common Findings**:
- SQL injection in raw queries
- XSS in template rendering
- CSRF token missing
- Weak Django SECRET_KEY
- DEBUG=True in production

---

### JavaScript + React + Node.js

```bash
# Frontend security scan
artemis scan src/ \
  --language javascript \
  --framework react \
  --check-xss \
  --check-dangerous-html

# Backend API security
artemis scan api/ \
  --language javascript \
  --framework express \
  --check-sql-injection \
  --check-auth

# Full-stack scan
artemis scan . --profile javascript-fullstack
```

**Common Findings**:
- Dangerously setting inner HTML
- Prototype pollution
- NoSQL injection
- JWT misconfiguration
- CORS misconfiguration

---

### Go + Kubernetes

```bash
# Go application scan
artemis scan . --language go

# Kubernetes manifest validation
demeter validate k8s/ \
  --check-security-context \
  --check-network-policies \
  --check-rbac

# Runtime container monitoring
hades monitor --kubernetes --namespace production
```

**Common Findings**:
- Running containers as root
- Missing security contexts
- Overly permissive RBAC
- Unencrypted secrets
- Missing network policies

---

### Java + Spring Boot

```bash
# Java security scan
artemis scan . \
  --language java \
  --framework spring-boot \
  --check-injection \
  --check-deserialization

# Dependency vulnerability check
artemis dependencies \
  --ecosystem maven \
  --check-cve
```

**Common Findings**:
- SQL injection in JDBC
- Insecure deserialization
- Path traversal
- XML external entity (XXE)
- Log4Shell vulnerabilities

---

## Team Size Scenarios

### 👤 **Solo Developer**

**Focus**: Quick feedback, minimal setup

```bash
# Quick pre-commit checks
artemis scan --quick

# Generate simple report
artemis report --format console
```

**Recommended Modules**: ARTEMIS only

---

### 👥 **Small Team (2-10)**

**Focus**: Collaboration, PR reviews

```yaml
# .github/workflows/security.yml
on: pull_request
jobs:
  security:
    - uses: horizonsec/artemis-action@v1
    - uses: horizonsec/comment-action@v1
```

**Recommended Modules**: ARTEMIS + DEMETER

---

### 👨‍👩‍👧‍👦 **Medium Team (10-50)**

**Focus**: Consistency, compliance

```yaml
# Use GAIA for orchestration
modules:
  artemis:
    enabled: true
    config: .artemis.yml
    
  demeter:
    enabled: true
    config: .demeter.yml
    
gates:
  security_threshold:
    max_critical: 0
    max_high: 5
    
notifications:
  slack: true
  jira_integration: true
```

**Recommended Modules**: Full suite (GAIA + ARTEMIS + DEMETER + HADES)

---

### 🏢 **Large Team (50+)**

**Focus**: Scale, governance, metrics

```yaml
# Enterprise-grade configuration
gaia:
  projects:
    - name: "frontend"
      modules: [artemis]
      
    - name: "backend"
      modules: [artemis, hades]
      
    - name: "infrastructure"
      modules: [demeter]
      
  reporting:
    aggregated: true
    dashboard: true
    metrics: true
    
  integrations:
    jira: true
    slack: true
    pagerduty: true
    siem: true
```

**Recommended Modules**: Full suite with custom integrations

---

## Advanced Workflows

### 📊 **Security Dashboard & Metrics**

```bash
# Start GAIA dashboard
gaia dashboard --port 8080

# Export metrics to Prometheus
gaia metrics export --format prometheus

# Generate trend reports
gaia report trends --days 30 --output trends.html
```

---

### 🔄 **Scheduled Security Audits**

```bash
# Cron job for nightly scans
0 2 * * * cd /app && gaia scan --full --report-email security@company.com
```

---

### 🎓 **Developer Security Training**

```bash
# Interactive security training mode
artemis scan --explain --interactive

# Generate security report cards
artemis report card --developer alice@company.com
```

---

## Integration Examples

### Jira Integration

```yaml
# Auto-create Jira tickets for findings
notifications:
  jira:
    url: "https://company.atlassian.net"
    project: "SEC"
    issue_type: "Security Bug"
    severity_mapping:
      critical: "Highest"
      high: "High"
      medium: "Medium"
      low: "Low"
```

---

### Slack Notifications

```yaml
notifications:
  slack:
    webhook: "${SLACK_WEBHOOK}"
    channels:
      critical: "#security-urgent"
      high: "#security"
      medium: "#dev-team"
    message_template: |
      :warning: Security Finding
      Severity: {severity}
      Issue: {title}
      File: {file}:{line}
      Fix: {recommendation}
```

---

## Success Stories

### Startup: 80% Reduction in Security Review Time

*"Before HorizonSec, security reviews delayed our releases by days. Now, we catch issues in CI/CD and reviews focus on architecture instead of basic vulnerabilities."*

**Setup**:
- ARTEMIS in GitHub Actions
- DEMETER for infrastructure validation
- Automated PR comments

**Results**:
- 80% faster security reviews
- 95% of issues caught before review
- Developer security awareness improved

---

### Mid-Size Company: Achieved SOC 2 Compliance

*"HorizonSec helped us document our security controls and prove continuous security testing for our SOC 2 audit."*

**Setup**:
- Full GAIA orchestration
- Daily compliance scans
- Audit trail and reporting

**Results**:
- Passed SOC 2 Type II audit
- Automated evidence collection
- Reduced audit prep time by 60%

---

## Ready to Try It Yourself?

Explore these examples in our repository:
- [Example Projects](https://github.com/HorizonSec/examples)
- [Configuration Templates](https://github.com/HorizonSec/horizon-documentation/tree/main/examples)
- [Video Tutorials](#) (Coming Soon)

---

*Have a use case we didn't cover? [Share it with the community](#) or [request an example](#)!*
