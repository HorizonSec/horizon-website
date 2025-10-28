# Community & Contributing

The HorizonSec Project is built by the community, for the community. Whether you're a seasoned security expert or just getting started with application security, there's a place for you here.

---

## Join Our Community

### 💬 **Discord Server**

Our primary hub for real-time discussions, support, and collaboration.

**Channels include:**
- `#general` - General discussions and introductions
- `#help` - Get support from the community
- `#development` - Development discussions and coordination
- `#security-research` - Share findings and research
- `#showcase` - Show off your projects using HorizonSec
- Module-specific channels (`#artemis`, `#demeter`, `#hades`, `#gaia`)

[**Join our Discord →**](#)

---

### 📣 **GitHub Discussions**

For longer-form discussions, RFCs (Request for Comments), and feature proposals.

**Categories:**
- **Announcements**: Release notes and project updates
- **Ideas**: Feature requests and brainstorming
- **Q&A**: Questions and answers about using HorizonSec
- **Show and Tell**: Share your implementations and use cases
- **RFCs**: Propose and discuss major changes

[**Start a Discussion →**](https://github.com/orgs/HorizonSec/discussions)

---

### 🐦 **Social Media**

Stay updated with the latest news:
- Twitter: [@HorizonSecProject](#)
- LinkedIn: [HorizonSec Project](#)
- Mastodon: [@horizonsec@infosec.exchange](#)

---

### 📧 **Newsletter**

Monthly updates on releases, tutorials, and community highlights.

[**Subscribe →**](#) (Coming Soon)

---

## Ways to Contribute

You don't need to be a security expert or write code to contribute! Here are all the ways you can help:

### 🐛 **Report Bugs**

Found something broken? Let us know!

1. Check if the issue already exists in [GitHub Issues](https://github.com/HorizonSec)
2. Create a new issue with details:
   - Steps to reproduce
   - Expected vs. actual behavior
   - Environment details (OS, version, configuration)
   - Error messages or logs

---

### 💡 **Suggest Features**

Have an idea for improvement?

1. Open a GitHub Discussion in the "Ideas" category
2. Describe the problem you're trying to solve
3. Propose your solution
4. Discuss with the community

For major features, we encourage RFCs (see below).

---

### 📝 **Improve Documentation**

Documentation is crucial for adoption and usability.

**Ways to help:**
- Fix typos and clarify confusing sections
- Add code examples and tutorials
- Create guides for specific use cases
- Translate documentation to other languages
- Record video tutorials

All documentation lives in the [`horizon-documentation`](https://github.com/HorizonSec/horizon-documentation) repository.

---

### 💻 **Write Code**

Contribute to the codebase by:
- Fixing bugs
- Implementing new features
- Improving performance
- Adding tests
- Refactoring for clarity

See our [Development Guide](#development-guide) below.

---

### 🧪 **Test & Provide Feedback**

Help us identify issues before release:
- Test alpha/beta releases
- Verify bug fixes
- Validate feature implementations
- Share your experience using HorizonSec in production

---

### 🎨 **Design & UX**

Improve the user experience:
- Design better CLI output formats
- Create dashboard mockups
- Improve error messages
- Enhance documentation visuals
- Design community assets (logos, banners, etc.)

---

### 🗣️ **Advocate & Educate**

Spread the word:
- Write blog posts about your experience
- Give talks at meetups or conferences
- Create video tutorials
- Answer questions on Stack Overflow
- Share on social media

---

### 🤝 **Help Others**

Support the community:
- Answer questions in Discord
- Review pull requests
- Welcome new contributors
- Mentor newcomers
- Share your expertise

---

## Development Guide

### Setting Up Your Development Environment

**Prerequisites:**
- Git
- Node.js 16+ (for Node-based modules)
- Python 3.8+ (for Python-based modules)
- Docker (optional, for testing)

**Fork and Clone:**
```bash
# Fork the repository on GitHub, then clone your fork
git clone https://github.com/YOUR_USERNAME/REPO_NAME.git
cd REPO_NAME

# Add upstream remote
git remote add upstream https://github.com/HorizonSec/REPO_NAME.git
```

**Install Dependencies:**
```bash
# For Node.js projects
npm install

# For Python projects
pip install -e ".[dev]"
```

**Run Tests:**
```bash
# Node.js
npm test

# Python
pytest
```

---

### Development Workflow

1. **Create a Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make Your Changes**
   - Write clear, documented code
   - Follow existing code style
   - Add tests for new functionality

3. **Test Your Changes**
   ```bash
   npm test  # or pytest
   npm run lint  # ensure code style compliance
   ```

4. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "Add feature: brief description"
   ```
   
   Follow [Conventional Commits](https://www.conventionalcommits.org/):
   - `feat:` - New feature
   - `fix:` - Bug fix
   - `docs:` - Documentation changes
   - `test:` - Adding or updating tests
   - `refactor:` - Code refactoring
   - `chore:` - Maintenance tasks

5. **Push and Create Pull Request**
   ```bash
   git push origin feature/your-feature-name
   ```
   
   Then create a PR on GitHub with:
   - Clear description of changes
   - Reference to related issues
   - Screenshots/demos if applicable

---

### Code Style Guidelines

**General Principles:**
- Write clear, self-documenting code
- Keep functions small and focused
- Use meaningful variable and function names
- Comment complex logic
- Avoid premature optimization

**Language-Specific:**

**JavaScript/TypeScript:**
- Use ESLint with our configuration
- Prefer async/await over callbacks
- Use TypeScript for new code

**Python:**
- Follow PEP 8
- Use type hints
- Document functions with docstrings

---

### Testing Requirements

All code changes must include tests:

- **Unit Tests**: Test individual functions and classes
- **Integration Tests**: Test module interactions
- **End-to-End Tests**: Test complete workflows

**Coverage Requirements:**
- Minimum 80% code coverage
- All new features must be tested
- Bug fixes should include regression tests

---

### Pull Request Process

1. **Before Submitting:**
   - Ensure all tests pass
   - Update documentation
   - Add changelog entry if applicable
   - Rebase on latest `main` branch

2. **PR Description:**
   - Describe what changes you made and why
   - Link to related issues
   - Include screenshots for UI changes
   - Note any breaking changes

3. **Review Process:**
   - At least one maintainer approval required
   - Address review feedback promptly
   - Keep discussions respectful and constructive

4. **After Approval:**
   - Maintainers will merge your PR
   - Changes will be included in next release

---

## RFC (Request for Comments) Process

For significant changes, we use an RFC process:

### When to Write an RFC

- New modules or major features
- Breaking API changes
- Significant architectural decisions
- Changes to project governance

### RFC Template

```markdown
# RFC: [Title]

## Summary
Brief description of the proposal.

## Motivation
Why are we doing this? What problem does it solve?

## Detailed Design
How will this work? Include examples, APIs, and implementation details.

## Drawbacks
What are the potential downsides?

## Alternatives
What other approaches were considered?

## Adoption Strategy
How will this be rolled out? Any migration path needed?

## Unresolved Questions
What aspects need further discussion?
```

### RFC Process

1. Create a GitHub Discussion in the "RFCs" category
2. Community discussion (minimum 1 week)
3. Incorporate feedback and iterate
4. Maintainers make final decision
5. RFC is accepted or rejected
6. If accepted, implementation begins

---

## Code of Conduct

### Our Pledge

We are committed to providing a welcoming and inclusive environment for everyone, regardless of:
- Age, body size, disability, ethnicity
- Gender identity and expression
- Level of experience, education
- Nationality, personal appearance, race, religion
- Sexual identity and orientation

### Our Standards

**Positive Behavior:**
- Using welcoming and inclusive language
- Being respectful of differing viewpoints
- Gracefully accepting constructive criticism
- Focusing on what's best for the community
- Showing empathy towards others

**Unacceptable Behavior:**
- Harassment, trolling, or insulting comments
- Personal or political attacks
- Public or private harassment
- Publishing others' private information
- Unprofessional conduct

### Enforcement

Violations may result in:
1. Warning
2. Temporary ban
3. Permanent ban

Report violations to: [conduct@horizonsec.org](#) (placeholder)

---

## Recognition & Rewards

We value our contributors! Here's how we recognize contributions:

### **Contributors Page**
All contributors are listed on our website and in project READMEs.

### **Swag**
Active contributors receive HorizonSec merchandise (coming soon).

### **Maintainer Status**
Consistent, high-quality contributors may be invited to become maintainers.

### **Community Spotlight**
Monthly highlights of outstanding contributions in our newsletter and social media.

---

## Governance

### Project Structure

**Founders (4 members)**
- Provide strategic direction
- Make final decisions on major changes
- Ensure project sustainability

**Maintainers**
- Review and merge pull requests
- Triage issues
- Guide technical decisions
- Support the community

**Contributors**
- Everyone who has contributed code, docs, or other improvements

### Decision Making

- **Consensus**: Most decisions made through community consensus
- **Maintainer Vote**: Technical decisions require maintainer agreement
- **Founder Decision**: Strategic direction and governance changes

---

## Release Process

### Versioning

We follow [Semantic Versioning](https://semver.org/):
- **MAJOR**: Breaking changes
- **MINOR**: New features (backward compatible)
- **PATCH**: Bug fixes

### Release Cycle

- **Alpha/Beta**: Frequent releases for testing
- **Stable**: Monthly releases
- **LTS**: Planned for future (long-term support versions)

### Release Notes

Every release includes:
- New features
- Bug fixes
- Breaking changes
- Migration guides (if needed)
- Contributors list

---

## Resources for Contributors

### **Documentation**
- [Getting Started Guide](getting-started.md)
- [Architecture Overview](#)
- [API Reference](https://horizonsec.github.io/horizon-documentation)

### **Communication**
- [Discord Server](#) - Real-time chat
- [GitHub Discussions](https://github.com/orgs/HorizonSec/discussions) - Async discussions
- [Office Hours](#) - Weekly community calls (coming soon)

### **Tools**
- [GitHub Projects](https://github.com/orgs/HorizonSec/projects) - Roadmap and tasks
- [CI/CD Status](#) - Build and test status
- [Code Coverage](#) - Coverage reports

---

## Frequently Asked Questions

**Q: I'm new to open source. How do I start?**
Start with documentation improvements or bug reports. Check issues labeled `good-first-issue`.

**Q: How long does PR review take?**
Most PRs are reviewed within 2-3 business days. Larger changes may take longer.

**Q: Can I work on an open issue?**
Yes! Comment on the issue to let others know you're working on it.

**Q: What if my PR isn't accepted?**
We'll provide feedback. You can revise and resubmit, or we'll explain why it doesn't fit the project direction.

**Q: How do I become a maintainer?**
Consistent, high-quality contributions over several months, plus demonstration of good judgment and communication skills.

---

## Thank You

Every contribution, no matter how small, makes HorizonSec better. Thank you for being part of this journey to make security accessible and transparent for all builders.

**Let's build something great—together.** 🚀

---

*For specific questions, reach out in Discord or email [community@horizonsec.org](#) (placeholder)*
