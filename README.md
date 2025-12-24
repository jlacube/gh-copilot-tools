# GitHub Copilot Tools

A collection of GitHub Copilot customization files and agent configurations designed to enhance AI-assisted development workflows with advanced capabilities including extended thinking, research-first approaches, and specification-driven development.

## Overview

This repository provides:
- **Coding Standards**: Comprehensive guidelines for Python, JavaScript/TypeScript to help GitHub Copilot generate idiomatic code
- **Agent Configurations**: Nine specialized Claude 4.5/Sonnet agent modes optimized for different development workflows
- **Workflow Integration**: Agents designed to work together across the complete development lifecycle

## Documentation

- **[Agent Configurations](docs/agents.md)** - Detailed descriptions of all 9 agents with features and use cases
- **[Workflow Integration](docs/workflows.md)** - Scenarios, decision trees, and agent handoffs
- **[Installation & Usage](docs/installation.md)** - Setup instructions, prerequisites, and configuration
- **[Contributing](docs/contributing.md)** - Guidelines for adding languages and creating new agents

## Repository Structure

```
.github/
├── copilot-instructions.md          # Primary coding standards (Python, JS/TS)
├── copilot-instructions-full.md     # Extended coding standards
├── agents/                          # Agent configuration files
│   ├── idea-scout-1.0.agent.md
│   ├── spec-architect-1.0.agent.md
│   ├── spec-validator-1.0.agent.md
│   ├── tech-radar-1.0.agent.md
│   ├── spec-kitty-buddy-1.0.agent.md
│   ├── coding-buddy-1.3.agent.md
│   ├── retro-spec-architect-1.0.agent.md
│   ├── retro-spec-validator-1.0.agent.md
│   └── spec-steward-1.0.agent.md
└── buddy/                           # Working directory for agent logs
    ├── thinking_log.md
    ├── research_log.md
    ├── progress.md
    └── context.md
docs/                                # Documentation
├── agents.md                        # Agent descriptions
├── workflows.md                     # Workflow scenarios
├── installation.md                  # Setup guide
└── contributing.md                  # Contribution guidelines
.gitignore                           # Comprehensive multi-language exclusions
```

## Quick Start

### 1. Clone Repository
```bash
git clone https://github.com/jlacube/gh-copilot-tools.git
```

### 2. Copy Coding Standards
```bash
cp gh-copilot-tools/.github/copilot-instructions.md your-project/.github/
```

### 3. Copy Agent(s)
```bash
# Copy all agents
cp gh-copilot-tools/.github/agents/*.agent.md your-project/.github/agents/

# Or copy specific agent
cp gh-copilot-tools/.github/agents/coding-buddy-1.3.agent.md your-project/.github/agents/
```

### 4. Use in VS Code
- Open Chat view (Ctrl+Alt+I / Cmd+Option+I)
- Click agent picker dropdown
- Select your custom agent
- Start coding!

**Requirements**: VS Code 1.106+, GitHub Copilot Pro/Pro+/Business/Enterprise

## Coding Standards

### Purpose
Provide comprehensive context for GitHub Copilot to generate idiomatic code following industry-standard conventions.

### Coverage
- **Python**: PEP 8 compliance, type hints, docstrings, best practices
- **JavaScript/TypeScript**: Airbnb style guide, ES6+ features, TypeScript strict types

### Key Principles
- **Readability**: Optimize for readers, not writers
- **Consistency**: Language-specific naming conventions and formatting
- **Type Safety**: Leverage type systems (TypeScript, Python type hints)
- **Security**: Input validation, secure defaults, least privilege
- **Performance**: Profile before optimizing, choose appropriate algorithms

## Agent Quick Reference

| Agent | Phase | Best For |
|-------|-------|----------|
| **Idea Scout** | Pre-Planning | Problem exploration, market research, solution ideation |
| **Tech Radar** | Planning | Technology evaluation, version tracking, stack recommendations |
| **Spec Architect** | Planning | Requirements discovery, architecture design, spec generation |
| **Spec Validator** | Planning | Specification review, completeness validation, quality assessment |
| **Spec-Kitty Buddy** | Implementation | Structured development with work packages and quality gates |
| **Coding Buddy** | Implementation | General development, debugging, feature implementation |
| **Retro-Spec Architect** | Documentation | Legacy code analysis, reverse engineering specifications |
| **Retro-Spec Validator** | Documentation | Validating reverse-engineered specs against codebase |
| **Spec Steward** | Maintenance | Ongoing spec maintenance, architecture validation, drift detection |

**See [Agent Configurations](docs/agents.md) for detailed descriptions.**

## Workflow Decision Tree

**What are you building?**

```
┌─ Vague idea? → Idea Scout → Spec Architect → Spec-Kitty Buddy
│
├─ Clear requirements? → Spec Architect → Spec Validator → Spec-Kitty Buddy
│
├─ Legacy codebase? → Retro-Spec Architect → Retro-Spec Validator → Spec Steward
│
├─ Quick fix/feature? → Coding Buddy
│
├─ Need tech decision? → Tech Radar → Spec Architect
│
└─ Maintain docs? → Spec Steward
```

**See [Workflow Integration](docs/workflows.md) for complete scenarios.**

## Features & Benefits

### For Individual Developers
- **Consistent Code Quality**: Copilot generates code following established patterns
- **Deep Reasoning**: Extended thinking for complex problem-solving
- **Research Integration**: Automatic fetching of current best practices
- **Execution Validation**: Confidence that generated code actually works

### For Teams
- **Standardized Output**: All team members using Copilot get consistent style
- **Specification-Driven**: Clear requirements before implementation
- **Quality Gates**: Enforced review and validation processes
- **Documentation**: Automatic logging of decisions and research

### For Legacy Projects
- **Reverse Engineering**: Extract specs from undocumented codebases
- **Modernization Planning**: Understand existing systems before refactoring
- **Knowledge Transfer**: Document tribal knowledge in specifications

## License

MIT License - Copyright (c) 2025 Jerome Lacube

See [LICENSE](LICENSE) file for full text.

## Support

For issues, questions, or contributions:
- **Issues**: [Open an issue](https://github.com/jlacube/gh-copilot-tools/issues)
- **Contributing**: See [Contributing Guide](docs/contributing.md)

---

**Last Updated**: 2025-12-24  
**Version**: 2.0.0  
**Maintained By**: Jerome Lacube
