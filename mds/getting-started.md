# Getting Started with HorizonSec

Welcome to The HorizonSec Project! This guide will help you get up and running with our security tools quickly and easily.

---

## Quick Start

The fastest way to try HorizonSec is to run a single module in your project. We'll use **ARTEMIS** (Static Code Analysis) as an example:

```bash
# Install ARTEMIS CLI
npm install -g @horizonsec/artemis-cli

# Run a security scan on your project
artemis scan .

# View results
artemis report
```

That's it! You'll get a detailed security report for your codebase in seconds.

---

## Prerequisites

Before you begin, ensure you have:

- **Git**: Version control for cloning repositories
- **Node.js** (v16+) or **Python** (3.8+): Depending on which module you're using
- **Docker** (optional): For containerized deployments
- **Access to your project**: Local or remote Git repository

---

## Installation Options

### Option 1: CLI Installation (Recommended for Getting Started)

Each HorizonSec module provides a standalone CLI tool:

**ARTEMIS (Static Code Analysis)**
```bash
# npm
npm install -g @horizonsec/artemis-cli

# pip
pip install horizonsec-artemis
```

**DEMETER (Infrastructure Scan)**
```bash
# npm
npm install -g @horizonsec/demeter-cli

# pip
pip install horizonsec-demeter
```

**HADES (Endpoint Security)**
```bash
# pip
pip install horizonsec-hades
```

**GAIA (Orchestration Framework)**
```bash
# npm
npm install -g @horizonsec/gaia-cli

# pip
pip install horizonsec-gaia
```

---

### Option 2: Docker Images

Run any module as a container:

```bash
# Pull the image
docker pull ghcr.io/horizonsec/artemis:latest

# Run a scan
docker run -v $(pwd):/workspace ghcr.io/horizonsec/artemis:latest scan /workspace
```

---

### Option 3: Source Installation

Build from source for the latest features:

```bash
# Clone the repository
git clone https://github.com/HorizonSec/artemis.git
cd artemis

# Install dependencies
npm install  # or: pip install -e .

# Run from source
npm start scan .  # or: python -m artemis scan .
```

---

## Your First Security Scan

Let's walk through running your first security scan with ARTEMIS:

### Step 1: Initialize Configuration

```bash
# Create a default configuration file
artemis init
```

This creates `.artemis.yml` in your project root with sensible defaults.

### Step 2: Run a Scan

```bash
# Scan your entire project
artemis scan .

# Scan specific directories
artemis scan src/ lib/

# Scan specific files
artemis scan src/app.py src/utils.py
```

### Step 3: Review Results

```bash
# View a summary report
artemis report

# Generate detailed HTML report
artemis report --format html --output security-report.html

# Export as JSON for further processing
artemis report --format json --output findings.json
```

---

## Configuration

HorizonSec modules use YAML configuration files. Here's a basic example:

```yaml
# .artemis.yml
version: "1.0"

# Scan settings
scan:
  exclude:
    - "node_modules/**"
    - "vendor/**"
    - "*.test.js"
  
  include:
    - "src/**"
    - "lib/**"

# Severity thresholds
thresholds:
  fail_on: "high"  # Fail if high or critical issues found
  warn_on: "medium"

# Rule configuration
rules:
  enable:
    - sql-injection
    - xss
    - hardcoded-secrets
  
  disable:
    - experimental-*

# Output preferences
output:
  format: "table"  # table, json, html, sarif
  verbose: true
  show_snippets: true
```

---

## CI/CD Integration

### GitHub Actions

Create `.github/workflows/security-scan.yml`:

```yaml
name: HorizonSec Security Scan

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
      
      - name: Run ARTEMIS Security Scan
        uses: horizonsec/artemis-action@v1
        with:
          fail-on-severity: high
          
      - name: Upload Results
        uses: github/codeql-action/upload-sarif@v2
        if: always()
        with:
          sarif_file: artemis-results.sarif
```

---

### GitLab CI

Add to your `.gitlab-ci.yml`:

```yaml
security-scan:
  stage: test
  image: ghcr.io/horizonsec/artemis:latest
  script:
    - artemis scan .
    - artemis report --format json --output gl-sast-report.json
  artifacts:
    reports:
      sast: gl-sast-report.json
    when: always
    expire_in: 1 week
```

---

### Jenkins

```groovy
pipeline {
    agent any
    
    stages {
        stage('Security Scan') {
            steps {
                sh 'npm install -g @horizonsec/artemis-cli'
                sh 'artemis scan .'
                
                publishHTML([
                    reportName: 'Security Report',
                    reportDir: '.',
                    reportFiles: 'security-report.html'
                ])
            }
        }
    }
}
```

---

## Using Multiple Modules

### Standalone Usage

Run each module independently:

```bash
# Static code analysis
artemis scan .

# Infrastructure scan
demeter scan --provider aws --region us-east-1

# Endpoint security (runtime)
hades monitor --container my-app
```

---

### Orchestrated with GAIA

Use GAIA to run all modules together:

```yaml
# gaia-config.yml
version: "1.0"

modules:
  artemis:
    enabled: true
    config: .artemis.yml
  
  demeter:
    enabled: true
    provider: aws
    regions:
      - us-east-1
      - eu-west-1
  
  hades:
    enabled: true
    targets:
      - type: container
        name: my-app

output:
  consolidated: true
  format: html
  destination: ./security-report/
```

```bash
# Run comprehensive scan
gaia scan --config gaia-config.yml
```

---

## Understanding Results

### Severity Levels

HorizonSec uses standard severity classifications:

- **Critical**: Immediate action required, actively exploitable
- **High**: Serious security risk, should be addressed soon
- **Medium**: Moderate risk, address in upcoming sprint
- **Low**: Minor issue, address when convenient
- **Info**: Informational finding, not a vulnerability

---

### Finding Format

Each security finding includes:

```json
{
  "id": "ARTEMIS-SQL-001",
  "severity": "high",
  "confidence": "high",
  "title": "SQL Injection Vulnerability",
  "description": "User input is directly concatenated into SQL query",
  "location": {
    "file": "src/database.py",
    "line": 45,
    "column": 12,
    "function": "get_user"
  },
  "snippet": "query = f\"SELECT * FROM users WHERE id = {user_id}\"",
  "recommendation": "Use parameterized queries or prepared statements",
  "references": [
    "https://owasp.org/www-community/attacks/SQL_Injection",
    "https://docs.horizonsec.org/artemis/sql-injection"
  ],
  "cwe": "CWE-89",
  "owasp": "A03:2021-Injection"
}
```

---

## Common Use Cases

### Local Development

```bash
# Quick security check before committing
artemis scan src/ --quick

# Detailed analysis with explanations
artemis scan . --verbose --explain
```

---

### Pre-Commit Hook

Add to `.git/hooks/pre-commit`:

```bash
#!/bin/bash
artemis scan --quick --fail-on high
if [ $? -ne 0 ]; then
    echo "Security issues found. Commit blocked."
    exit 1
fi
```

---

### Security Review

```bash
# Full comprehensive scan with detailed report
artemis scan . --deep --output-format html

# Check dependencies for vulnerabilities
artemis dependencies --check-cve
```

---

### Continuous Monitoring

```bash
# Set up cron job for daily scans
0 2 * * * cd /path/to/project && artemis scan . --email-report security@company.com
```

---

## Troubleshooting

### Common Issues

**Issue**: "Command not found: artemis"
```bash
# Solution: Ensure installation path is in PATH
export PATH="$PATH:$(npm bin -g)"  # for npm
# or
export PATH="$PATH:$HOME/.local/bin"  # for pip
```

**Issue**: "Permission denied"
```bash
# Solution: Run with appropriate permissions
sudo npm install -g @horizonsec/artemis-cli
# or
pip install --user horizonsec-artemis
```

**Issue**: "Rate limit exceeded"
```bash
# Solution: Use authentication token
export HORIZONSEC_TOKEN="your-token-here"
artemis scan .
```

---

### Debug Mode

Enable verbose logging:

```bash
# Set debug environment variable
export HORIZONSEC_DEBUG=1

# Run with verbose flag
artemis scan . --verbose --debug
```

---

### Getting Help

- **Documentation**: [https://horizonsec.github.io/horizon-documentation](https://horizonsec.github.io/horizon-documentation)
- **Discord**: Join our community for real-time support
- **GitHub Issues**: Report bugs or request features
- **Stack Overflow**: Tag questions with `horizonsec`

---

## Next Steps

Now that you're up and running:

1. **[Configure Your Scans](#)** - Customize rules and thresholds
2. **[Explore Advanced Features](features.md)** - Learn about all capabilities
3. **[Set Up CI/CD Integration](#)** - Automate security in your pipeline
4. **[Join the Community](#)** - Connect with other builders
5. **[Contribute](#)** - Help make HorizonSec better

---

## Quick Reference

### Essential Commands

```bash
# ARTEMIS (Static Code Analysis)
artemis init                    # Create config file
artemis scan .                  # Scan project
artemis report                  # View results
artemis dependencies            # Check dependencies

# DEMETER (Infrastructure)
demeter scan                    # Scan infrastructure
demeter validate terraform/     # Validate IaC
demeter check-compliance        # Run compliance checks

# HADES (Endpoint Security)
hades monitor                   # Start monitoring
hades status                    # Check status
hades incidents                 # View incidents

# GAIA (Orchestration)
gaia scan                       # Run all modules
gaia dashboard                  # Open web dashboard
gaia export                     # Export results
```

---

### Configuration Files

- `.artemis.yml` - ARTEMIS configuration
- `.demeter.yml` - DEMETER configuration
- `.hades.yml` - HADES configuration
- `gaia-config.yml` - GAIA orchestration config

---

### Environment Variables

```bash
HORIZONSEC_DEBUG=1              # Enable debug logging
HORIZONSEC_TOKEN=xxx            # Authentication token
HORIZONSEC_CONFIG=path          # Custom config path
HORIZONSEC_OUTPUT=json          # Default output format
```

---

*Ready to secure your applications? Start scanning and make security transparent!*
