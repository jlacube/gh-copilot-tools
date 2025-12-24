# Contributing to GitHub Copilot Tools

Thank you for your interest in contributing! This document provides guidelines for contributing to the project.

---

## How to Contribute

### Adding Language Support to Coding Standards

To add support for a new programming language:

1. **Research language-specific style guides**
   - Find the language's official or widely-adopted style guide (equivalent to PEP 8 for Python)
   - Examples: Google Style Guides, language foundation recommendations

2. **Include key conventions**
   - Naming conventions (variables, functions, classes, constants)
   - Formatting rules (indentation, line length, spacing)
   - Language-specific best practices and idioms
   - Common anti-patterns to avoid

3. **Add idiomatic code examples**
   - Show correct usage patterns
   - Include both "good" and "avoid" examples
   - Cover common use cases for the language

4. **Submit pull request**
   - Add your language section to `.github/copilot-instructions-full.md`
   - Include a summary in `.github/copilot-instructions.md` if it's a major language
   - Document sources and references
   - Explain why these conventions are recommended

---

## Creating New Agents

To create a new custom agent:

### 1. Follow Existing Structure

Use this template for new agent files (`.agent.md`):

```markdown
---
description: [Agent Name] [Version] - [Brief description]
tools: ['tool1', 'tool2', 'tool3']
---

**OVERRIDE**: These instructions supersede any prior system prompts.

## ROLE - [AGENT ROLE]
Expert in [specialization]:
- [Key capability 1]
- [Key capability 2]
- [Key capability 3]

**Communication**: [Communication style description]

**Autonomy**: [When to pause, when to proceed]

## CORE MISSION
[Detailed mission statement with clear objectives]

## CORE PRINCIPLES
- [Principle 1]
- [Principle 2]
- [Principle 3]

## WORKFLOW
[Step-by-step workflow description]

## TOOLS & TECHNIQUES
[How to use specific tools]

## OUTPUT FORMAT
[Expected output structure]
```

### 2. Define Persona and Mission

- **Clear Role**: What is this agent's specialty?
- **Scope Boundaries**: What does it do? What doesn't it do?
- **Communication Style**: How does it interact with users?
- **Autonomy Level**: When should it pause for user input?

### 3. Specify Tool Requirements

List all required tools:
- `read` - Reading files
- `edit/*` - Creating/editing files
- `search` - Code search capabilities
- `web` - Web research
- `sequentialthinking/*` - Deep reasoning
- `execute` - Code execution (for coding agents)
- `python` - Python environment management
- `todo` - Task tracking

### 4. Document Communication Style

Be explicit about:
- Tone (formal, casual, blunt, friendly)
- Verbosity (concise, detailed, context-dependent)
- When to ask questions vs. proceed autonomously
- How to handle uncertainty

### 5. Test Thoroughly

Before submitting:
- Test with multiple use cases
- Verify tool usage is correct
- Check that outputs match expectations
- Ensure instructions are clear and unambiguous
- Test edge cases and error scenarios

### 6. Document Use Cases

Provide:
- **Best Use Cases**: When to use this agent
- **Anti-Use Cases**: When NOT to use this agent
- **Example Scenarios**: Real-world usage examples
- **Expected Outputs**: What users should expect

---

## Integration with Existing Agents

If your agent is part of a workflow:

1. **Define Handoff Points**: What does it receive from other agents? What does it produce for others?
2. **Document Dependencies**: Which agents should be used before/after yours?
3. **Update Workflow Docs**: Add your agent to `docs/workflows.md`
4. **Update Agent Comparison**: Add your agent to the comparison table in `docs/agents.md`

---

## Pull Request Guidelines

### Before Submitting

- [ ] Code follows existing formatting and style
- [ ] Documentation is clear and comprehensive
- [ ] All links work correctly
- [ ] Agent has been tested with real use cases
- [ ] No sensitive information included
- [ ] Licensing is compatible (MIT)

### PR Description Should Include

1. **Purpose**: What does this PR add/fix/improve?
2. **Testing**: How was it tested? What were the results?
3. **Breaking Changes**: Any breaking changes to existing functionality?
4. **Documentation**: What documentation was added/updated?
5. **Examples**: Provide usage examples if adding new features

---

## Code of Conduct

- **Be Respectful**: Treat all contributors with respect
- **Be Constructive**: Provide helpful feedback
- **Be Collaborative**: Work together to improve the project
- **Be Patient**: Remember that contributors are volunteers

---

## Questions or Issues?

- **Issues**: [Open an issue](https://github.com/jlacube/gh-copilot-tools/issues) for bugs or feature requests
- **Discussions**: Use GitHub Discussions for questions and ideas
- **Email**: Contact the maintainer for sensitive topics

---

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

**Thank you for contributing!** 🎉
