# Frequently Asked Questions

Find answers to common questions about The HorizonSec Project, our tools, and how to get involved.

---

## General Questions

### What is The HorizonSec Project?

The HorizonSec Project is an open-source security framework designed to make application security transparent, actionable, and accessible to builders of all levels. We provide modular security tools that integrate directly into your development workflow, offering static code analysis, infrastructure scanning, endpoint security, and orchestration capabilities.

---

### Who is HorizonSec for?

HorizonSec is built for **everyone who builds software**:
- Solo developers building side projects
- Small teams at startups
- Engineering teams at mid-size companies
- Enterprise development organizations
- Security teams looking for open-source alternatives
- DevOps engineers embedding security in CI/CD

If you write code or manage infrastructure, HorizonSec is for you.

---

### Is HorizonSec really free?

**Yes, completely free.** HorizonSec is licensed under the MIT License, which means:
- Free to use for any purpose (personal, commercial, enterprise)
- Free to modify and distribute
- No hidden costs or premium tiers
- No feature gating or "enterprise-only" capabilities
- No required registration or license keys

We believe security should be accessible to everyone.

---

### What makes HorizonSec different from other security tools?

**1. Truly Open Source**: No bait-and-switch. Everything is MIT licensed with full source code available.

**2. Modular Architecture**: Use individual modules independently or combine them. Start small, scale up.

**3. Builder-First Design**: Designed for developers, not security specialists. Clear, actionable feedback instead of cryptic reports.

**4. Multi-Cloud Native**: Works across AWS, GCP, Azure, and on-premises without vendor lock-in.

**5. CI/CD Integration**: Native support for GitHub Actions, GitLab CI, Jenkins, and more—security at the speed of development.

**6. Ephemeral Security Sandboxes**: Test in isolated environments without affecting your systems.

---

### How does HorizonSec compare to [Commercial Tool X]?

We're not trying to replace enterprise solutions—we're providing an accessible alternative. Here's how we differ:

| Feature | HorizonSec | Commercial Tools |
|---------|------------|------------------|
| Cost | Free (MIT) | $$$-$$$$ per user/year |
| Source Code | Fully open | Proprietary |
| Deployment | Self-hosted | Cloud-based (usually) |
| Customization | Full control | Limited |
| Data Privacy | Your infrastructure | Their cloud |
| Feature Gating | None | Common |
| Community | Open collaboration | Vendor support |

**Use HorizonSec if**: You want control, transparency, and don't want to pay per-seat licensing.

**Use Commercial Tools if**: You need dedicated 24/7 support contracts or compliance certifications that require vendor backing.

---

### What's the project status?

All four core modules are currently in **active development (alpha stage)**. We're building in the open and welcoming early adopters and contributors.

- **ARTEMIS (Static Analysis)**: Expected alpha Q1 2025
- **DEMETER (Infrastructure)**: Expected alpha Q2 2025
- **GAIA (Orchestration)**: Expected alpha Q2 2025
- **HADES (Endpoint Security)**: Expected alpha Q3 2025

See our [Roadmap](roadmap.md) for detailed timeline.

---

## Technical Questions

### What languages and frameworks does ARTEMIS support?

**Currently in development:**
- Python
- JavaScript/TypeScript
- Node.js frameworks (Express, Nest.js, etc.)

**Planned for 2025:**
- Java
- Go
- Ruby
- PHP
- C/C++
- Rust
- C#/.NET

See [Roadmap](roadmap.md) for specific timelines.

---

### What cloud providers does DEMETER support?

**Current focus:**
- AWS (most comprehensive)

**Coming in 2025:**
- Google Cloud Platform (Q2 2025)
- Microsoft Azure (Q3 2025)
- On-premises infrastructure
- Hybrid environments

---

### Can I use HorizonSec in production?

**Not yet.** We're in alpha development. Current builds are for:
- Testing and evaluation
- Development and staging environments
- Providing feedback to the project

**Production use is planned for late 2025** after:
- Extensive testing and hardening
- Security audits
- Performance optimization
- Comprehensive documentation
- Stable release versions

---

### Does HorizonSec replace penetration testing?

**No.** HorizonSec automates many security checks and catches common vulnerabilities, but it doesn't replace:
- Manual penetration testing
- Security code reviews by experts
- Red team assessments
- Compliance audits

Think of HorizonSec as **continuous security testing** that complements (not replaces) these activities.

---

### How does HorizonSec handle false positives?

We prioritize **signal over noise**:

1. **High-Confidence Rules**: Focus on validated detection patterns
2. **Contextual Analysis**: Understand how code is actually used
3. **Suppression Mechanism**: Mark false positives to ignore them
4. **Community Feedback**: Learn from real-world usage
5. **Custom Rules**: Tune detection for your specific needs

We're continuously improving detection accuracy based on community feedback.

---

### Can I customize the security rules?

**Yes!** Each module supports:
- **Rule configuration**: Enable/disable specific checks
- **Severity adjustment**: Change how issues are classified
- **Custom rules**: Write your own detection patterns
- **Policy as code**: Version-control your security policies
- **Team profiles**: Different rules for different projects

---

### What about data privacy and security?

**Your data stays yours:**
- **Self-hosted**: Run on your own infrastructure
- **No telemetry by default**: We don't collect usage data unless you opt-in
- **No external dependencies**: Core functionality doesn't require internet access
- **Air-gap compatible**: Works in isolated environments
- **Encrypted communication**: When modules communicate

We take security seriously—especially for a security tool!

---

### How does HorizonSec integrate with my CI/CD pipeline?

We provide native integrations for:

- **GitHub Actions**: Pre-built workflow actions
- **GitLab CI**: Pipeline templates
- **Jenkins**: Plugins and Jenkinsfiles
- **CircleCI**: Orbs
- **Azure DevOps**: Pipeline tasks
- **Bitbucket Pipelines**: Pipe components
- **Generic CI/CD**: CLI tools and Docker images

See [Getting Started](getting-started.md) for integration guides.

---

## Usage Questions

### How long does a scan take?

Depends on project size and module:

**ARTEMIS (Static Analysis)**
- Small project (<10k LOC): ~30 seconds
- Medium project (10k-100k LOC): 1-5 minutes
- Large project (100k+ LOC): 5-15 minutes

**DEMETER (Infrastructure)**
- Small deployment (<50 resources): ~1 minute
- Medium deployment (50-500 resources): 2-5 minutes
- Large deployment (500+ resources): 5-15 minutes

**Performance optimizations** like incremental scanning and parallelization are in progress.

---

### Can I use HorizonSec locally during development?

**Absolutely!** Each module provides:
- CLI tools for local development
- Pre-commit hooks
- IDE extensions (coming soon)
- Fast feedback during coding

Security testing shouldn't wait for CI/CD.

---

### What output formats are supported?

All modules support:
- **Console/Terminal**: Human-readable tables and summaries
- **JSON**: Machine-readable for automation
- **HTML**: Detailed reports with styling
- **SARIF**: Standard format for tool integration
- **CSV**: For spreadsheet analysis
- **Markdown**: Documentation-friendly format

---

### Can I integrate HorizonSec with my issue tracker?

**Yes!** GAIA (orchestration module) will support:
- GitHub Issues
- GitLab Issues
- Jira
- Linear
- Asana
- Azure Boards
- Custom webhooks

---

### How do I suppress false positives?

Use inline comments or configuration files:

**Inline suppression:**
```python
# horizonsec: ignore sql-injection
query = f"SELECT * FROM {table_name}"
```

**Configuration file:**
```yaml
# .artemis.yml
suppressions:
  - rule: sql-injection
    file: src/legacy.py
    reason: "Validated by other means"
```

---

## Community & Contributing

### How can I contribute?

Many ways to help:
- 🐛 **Report bugs**: Found an issue? Let us know
- 💡 **Suggest features**: Share your ideas
- 💻 **Write code**: Fix bugs, add features
- 📝 **Improve docs**: Clarify, expand, translate
- 🧪 **Test releases**: Validate changes
- 🗣️ **Help others**: Answer questions, mentor newcomers
- 📢 **Spread the word**: Blog posts, talks, social media

See [Community & Contributing](community-contributing.md) for details.

---

### I'm new to open source. Where do I start?

**Perfect!** We welcome first-time contributors:

1. **Join Discord**: Introduce yourself in #general
2. **Read the docs**: Familiarize yourself with the project
3. **Find a task**: Look for issues labeled `good-first-issue`
4. **Ask questions**: Don't be shy—we're here to help
5. **Make a contribution**: Start small (fix typo, improve docs)

Everyone starts somewhere. We're here to support you.

---

### Do you accept financial contributions?

**Not yet**, but we're working on it. Future options may include:
- GitHub Sponsors
- Open Collective
- Patreon
- Corporate sponsorships

For now, the best way to support us is through code contributions, community participation, and advocacy.

---

### Can my company use HorizonSec?

**Yes!** The MIT License explicitly allows commercial use. You can:
- Use HorizonSec in commercial projects
- Modify it for internal needs
- Redistribute it with your products
- Deploy it for clients

No permission needed. No attribution required (though appreciated!).

---

### Will there be enterprise support?

**Potentially in the future.** We're exploring:
- Paid support contracts
- Professional services (consulting, training)
- Custom feature development
- SLA guarantees

The core project will always remain free and open source.

---

## Roadmap & Future

### When will v1.0 be released?

**Target: Late 2025 to Early 2026** for stable v1.0 releases of all modules.

Current timeline:
- Q1-Q2 2025: Alpha releases
- Q3-Q4 2025: Beta releases with stability focus
- H1 2026: v1.0 production-ready releases

See [Roadmap](roadmap.md) for detailed schedule.

---

### What features are coming next?

**Q1 2025:**
- ARTEMIS alpha release
- GitHub Actions integration
- Basic dependency scanning

**Q2 2025:**
- DEMETER alpha (AWS support)
- GAIA orchestration alpha
- GitLab CI integration

**Q3 2025:**
- Multi-language support expansion
- Multi-cloud support (GCP, Azure)
- HADES endpoint security alpha

See [Roadmap](roadmap.md) for complete timeline.

---

### Can I request a feature?

**Yes!** We encourage it:
1. Check if it's already been requested in GitHub Discussions
2. Open a new discussion in "Ideas" category
3. Describe the problem you're trying to solve
4. Propose your solution
5. Engage with community feedback

For major features, consider writing an RFC.

---

### How do you prioritize features?

Based on:
1. **Community demand**: How many people want it?
2. **Impact**: How much value does it provide?
3. **Effort**: How complex is the implementation?
4. **Strategic fit**: Does it align with our mission?
5. **Maintainability**: Can we support it long-term?

Community input heavily influences our priorities.

---

## Troubleshooting

### Installation isn't working. What should I do?

**Common solutions:**

1. **Check prerequisites**: Node.js 16+ or Python 3.8+
2. **Update tools**: `npm update -g` or `pip install --upgrade`
3. **Clear cache**: `npm cache clean --force` or `pip cache purge`
4. **Check permissions**: May need `sudo` or `--user` flag
5. **Review logs**: Enable debug mode for more info

Still stuck? Ask in Discord #help channel.

---

### The scan is taking too long. How can I speed it up?

**Tips:**
- **Exclude unnecessary files**: node_modules, build artifacts
- **Use incremental scans**: Only scan changed files
- **Increase parallelism**: Use `--parallel` flag
- **Run specific checks only**: Disable rules you don't need
- **Upgrade hardware**: More CPU/RAM helps

See [Getting Started](getting-started.md) for optimization tips.

---

### I'm getting too many false positives. What can I do?

1. **Adjust severity thresholds**: Focus on high/critical issues first
2. **Tune rules**: Disable problematic rules temporarily
3. **Use suppressions**: Mark known false positives
4. **Report issues**: Help us improve detection accuracy
5. **Share feedback**: Tell us what's not working

False positive reduction is a top priority.

---

### Where can I get help?

Multiple support channels:

- **Discord**: #help channel for real-time assistance
- **GitHub Issues**: Report bugs or technical problems
- **GitHub Discussions**: Q&A and community support
- **Documentation**: Comprehensive guides and references
- **Stack Overflow**: Tag questions with `horizonsec`

---

## Legal & Licensing

### What license does HorizonSec use?

**MIT License** for all modules. This means:
- Commercial use allowed
- Modification allowed
- Distribution allowed
- Private use allowed
- No liability or warranty
- Limited attribution required

See the LICENSE file in each repository for full text.

---

### Can I use HorizonSec in closed-source projects?

**Yes!** The MIT License doesn't require you to open-source your project. You can:
- Use HorizonSec to scan proprietary code
- Embed HorizonSec in commercial products
- Modify HorizonSec without publishing changes

---

### Do you have a Contributor License Agreement (CLA)?

**No.** We don't require a CLA. By contributing, you agree that:
- Your contributions are your original work
- You have the right to submit them
- Contributions are licensed under the same MIT License

Simple and straightforward.

---

### What about security vulnerabilities in HorizonSec?

**Security is paramount.** If you find a vulnerability:

1. **DO NOT** open a public issue
2. Email: [security@horizonsec.org](#) (placeholder)
3. Include detailed reproduction steps
4. We'll respond within 48 hours
5. We'll coordinate responsible disclosure

See SECURITY.md in each repository for details.

---

## Still Have Questions?

**We're here to help!**

- 💬 **Discord**: [Join our community server](#) - Fastest response
- 📧 **Email**: [contact@horizonsec.org](#) (placeholder)
- 🐛 **GitHub Issues**: For bug reports and technical questions
- 💭 **GitHub Discussions**: For longer discussions and Q&A
- 🐦 **Twitter**: [@HorizonSecProject](#) - For general updates

---

*Can't find your answer? Join our Discord and ask the community. We're always happy to help!*
