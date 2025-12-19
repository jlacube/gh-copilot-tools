# GitHub Copilot Tools

A collection of GitHub Copilot customization files and agent configurations designed to enhance AI-assisted development workflows with advanced capabilities including extended thinking, research-first approaches, and specification-driven development.

## Overview

This repository provides:
- **Coding Standards**: Comprehensive guidelines for Python, JavaScript/TypeScript to help GitHub Copilot generate idiomatic code
- **Agent Configurations**: Four specialized Claude 4.5/Sonnet agent modes optimized for different development workflows

## Repository Structure

```
.github/
├── copilot-instructions.md          # Primary coding standards (Python, JS/TS)
├── copilot-instructions-full.md     # Extended coding standards
└── agents/                          # Agent configuration files
    ├── coding-buddy-1.3-sonnet4.5-mcp.agent.md
    ├── spec-kitty-buddy-1.0-sonnet4.5-mcp.agent.md
    ├── spec-architect-1.0-sonnet4.5-mcp.agent.md
    └── retro-spec-architect-1.0-sonnet4.5-mcp.agent.md
.gitignore                           # Comprehensive multi-language exclusions
```

## Coding Standards

### Purpose
The coding standards files (`copilot-instructions.md` and `copilot-instructions-full.md`) provide comprehensive context for GitHub Copilot to generate code following industry-standard conventions.

### Coverage
- **Python**: PEP 8 compliance, type hints, docstrings, best practices
- **JavaScript/TypeScript**: Airbnb style guide, ES6+ features, TypeScript strict types

### Key Principles
- **Readability**: Optimize for readers, not writers
- **Consistency**: Language-specific naming conventions and formatting
- **Type Safety**: Leverage type systems (TypeScript, Python type hints)
- **Security**: Input validation, secure defaults, least privilege
- **Performance**: Profile before optimizing, choose appropriate algorithms

### Usage
Place these files in your `.github/` directory. GitHub Copilot automatically reads them as context when generating code suggestions.

## Agent Configurations

Four specialized agent modes for different development workflows, all Claude 4.5/Sonnet-optimized with extended thinking capabilities.

### Agent Comparison

| Agent | Primary Use Case | Code Execution | Research Focus | Best For |
|-------|-----------------|----------------|----------------|----------|
| **Coding Buddy 1.3** | General development & debugging | ✅ Yes | Extensive fetch research | Daily coding tasks, bug fixes, feature implementation |
| **Spec-Kitty Buddy 1.0** | Spec-Kitty workflow implementation | ✅ Yes | Fetch + mandatory 10+ Q&A | Structured feature development with work packages |
| **Spec Architect 1.0** | Requirements discovery & specs | ❌ No | Extensive fetch research | Greenfield projects, architecture design |
| **Retro-Spec Architect 1.0** | Legacy code analysis & docs | ❌ No | Code analysis tools | Documenting existing codebases, reverse engineering |

### 1. Coding Buddy 1.3
**File**: `coding-buddy-1.3-sonnet4.5-mcp.agent.md`

#### Description
General-purpose coding assistant with "God of All Developers" persona featuring 200+ years of cumulative experience.

#### Key Features
- **Extended Thinking**: Leverages Claude 4.5's 64K-200K token thinking budgets
- **Research-First**: Mandatory fetch operations from credible sources before implementation
- **Code Execution**: Zero tolerance for unexecuted code - runs everything before handoff
- **Real-time Tracking**: TODO lists and tracking files updated throughout execution
- **Timestamp Enforcement**: ISO 8601 timestamps on all entries
- **Skeptical Validation**: Fact-checks user claims before accepting them

#### Communication Style
Cold stone blunt. Direct, factual, no sugar coating. Challenges assumptions. Delivers truth over speed.

#### Best Use Cases
- Daily coding tasks across all languages/frameworks
- Bug fixes with root cause analysis
- Feature implementation with execution validation
- Code refactoring with comprehensive testing

### 2. Spec-Kitty Buddy 1.0
**File**: `spec-kitty-buddy-1.0-sonnet4.5-mcp.agent.md`

#### Description
Implementation agent enforcing Spec-Kitty workflow methodology with mandatory quality gates and batch Q&A.

#### Key Features
- **Mandatory Batch Q&A**: Minimum 10+ questions at discovery gates (enforced, not optional)
- **Work Package Management**: WPxx format with Txxx subtasks, lane tracking
- **Quality Gates**: Constitution check, accept validation before merge
- **Spec-Kitty Workflow**: Constitution → specify → plan → research → tasks → implement → review → accept
- **Activity Logging**: All actions tracked with timestamps in `.kittify/` directory
- **Code Execution**: MANDATORY for all generated code

#### Spec-Kitty Workflow Phases
1. **Constitution Check**: Verify project principles exist before feature work
2. **Discovery**: 10+ batch questions to understand requirements
3. **Specification**: Generate comprehensive specs in `.kittify/specs/`
4. **Planning**: Create work packages with subtasks
5. **Research**: Multi-source validation with fetch
6. **Implementation**: Incremental development with execution validation
7. **Review**: Code review against constitution
8. **Accept**: Final validation before merge

#### Best Use Cases
- Structured feature development with rigorous requirements
- Team projects requiring clear specifications
- Projects with quality gates and review processes
- Features requiring extensive upfront discovery

### 3. Spec Architect 1.0
**File**: `spec-architect-1.0-sonnet4.5-mcp.agent.md`

#### Description
Specification-focused architect for requirements discovery and comprehensive documentation generation. Does NOT execute code.

#### Key Features
- **Q&A-Driven Discovery**: 5-10 batch questions covering problem, scale, constraints, quality attributes
- **Architecture Design**: System structure, component interactions, technology selection
- **Specification Generation**: Functional specs, technical specs, data models, API contracts
- **Feature Identification**: Determines if projects should be split into multiple features
- **Technology Research**: Fetch-based research for optimal tech stack recommendations

#### Generated Specifications
For each feature, creates in `specs/<feature-name>/`:
- `functional_spec.md`: WHAT the feature does (requirements, user stories, workflows)
- `technical_spec.md`: HOW it's implemented (architecture, tech stack, data models)
- `api_spec.md`: API contracts, endpoints, request/response formats (if applicable)
- `testing_spec.md`: Test strategy, test cases, acceptance criteria

#### Best Use Cases
- Greenfield projects requiring comprehensive planning
- Brainstorming new application ideas
- Architecture design before implementation
- Creating detailed specifications for development teams

### 4. Retro-Spec Architect 1.0
**File**: `retro-spec-architect-1.0-sonnet4.5-mcp.agent.md`

#### Description
Reverse engineering specialist that analyzes legacy codebases and generates comprehensive specification documents. Does NOT execute or generate code.

#### Key Features
- **Codebase Discovery**: Automatic language/framework detection with user confirmation
- **Code Analysis Tools**: Extensive use of semantic_search and grep_search
- **Pattern Recognition**: Identifies design patterns, anti-patterns, architectural styles
- **Requirements Extraction**: Infers user requirements from implemented features
- **Architecture Mapping**: Documents existing system structure, components, interactions

#### Analysis Workflow
1. **Codebase Discovery**: Scan structure, detect languages/frameworks, identify exclusions
2. **Architecture Analysis**: Map layers, identify patterns, document dependencies
3. **Feature Extraction**: Identify distinct features, understand workflows
4. **Specification Generation**: Create comprehensive docs compatible with Spec-Kitty
5. **User Confirmation**: Required at critical decision points (folder selection, module boundaries)

#### Generated Specifications
Per module/feature in `retro-specs/<feature-name>/`:
- `reverse_engineered_spec.md`: Extracted requirements and implementation details
- `architecture_analysis.md`: System structure, patterns, technology stack
- `data_model_spec.md`: Database schemas, entities, relationships
- `api_spec.md`: Existing API contracts (if applicable)

#### Best Use Cases
- Documenting undocumented legacy codebases
- Reverse engineering specifications for rewrites
- Onboarding new developers to existing projects
- Creating specs before refactoring or modernization

## Core Capabilities (All Agents)

### Extended Thinking
- Claude 4.5's 64K-200K thinking token budgets leveraged for deep reasoning
- Sequential thinking sessions logged with timestamps
- Multiple thinking sessions per complex task

### Research-First Approach
- **Fetch tool intensive**: Minimum 5+ fetch operations from credible sources
- Multi-source validation (official docs, GitHub repos, Stack Overflow, MDN)
- Sequential fetch strategy: overview → specific docs → alternatives → common issues

### Comprehensive Logging
All agents maintain detailed logs (where applicable):
- `thinking_log.md`: All reasoning processes with timestamps and thinking budgets
- `research_log.md`: All fetch operations, queries, URLs, findings with timestamps
- `execution_log.md`: All code execution results with timestamps
- `progress.md`: Real-time TODO lists updated throughout execution

### Quality Enforcement
- **Timestamp Enforcement**: ISO 8601 format on all entries
- **Code Execution Validation**: Zero tolerance for unexecuted code (coding agents)
- **TODO Tracking**: Real-time updates throughout task execution
- **Sequential File Generation**: Avoid context limits with chunking strategy

### Communication Style
All agents share:
- **Cold stone blunt**: Direct, factual, no sugar coating
- **Skeptical validation**: Verify claims before accepting
- **Concise output**: Minimal words, maximum information density
- **God-tier expertise**: 200+ years cumulative experience persona

## Installation & Usage

### Prerequisites
- Visual Studio Code 1.106+ (for custom agents)
- GitHub Copilot extension
- **GitHub Copilot Pro, Pro+, Business, or Enterprise** (required for Claude Sonnet 4.5 and advanced models)
  - Free tier does NOT include Claude Sonnet 4.5
  - See [GitHub Copilot Plans](https://docs.github.com/en/copilot/about-github-copilot/plans-for-github-copilot) for model availability

### Setup

#### 1. Coding Standards
Copy coding standards to your project's `.github/` directory:
```bash
# Clone this repository
git clone https://github.com/yourusername/gh-copilot-tools.git

# Copy to your project
cp gh-copilot-tools/.github/copilot-instructions.md your-project/.github/
```

GitHub Copilot automatically reads `.github/copilot-instructions.md` as context.

#### 2. Agent Configurations
Agent files are VS Code custom agent configurations (`.agent.md` format). To use:

1. Copy desired agent file(s) to your project's `.github/agents/` directory:
   ```bash
   # Copy specific agent
   cp gh-copilot-tools/.github/agents/coding-buddy-1.3-sonnet4.5-mcp.agent.md your-project/.github/agents/
   
   # Or copy all agents
   cp gh-copilot-tools/.github/agents/*.agent.md your-project/.github/agents/
   ```

2. VS Code automatically detects `.agent.md` files in `.github/agents/`

3. **Switch to agent via agent picker dropdown**:
   - Open Chat view (Ctrl+Alt+I / Cmd+Option+I)
   - Click the agent picker dropdown (shows current agent name)
   - Select your custom agent from the list

4. Submit prompts as normal - the selected agent's instructions and tools apply automatically

**Note:** Custom agents require VS Code 1.106+ and GitHub Copilot extension.

### Configuration

#### Coding Standards Customization
Edit `.github/copilot-instructions.md` to add:
- Language-specific guidelines for your tech stack
- Project-specific conventions and patterns
- Team coding standards and preferences

#### Agent Customization
Modify agent `.md` files to adjust:
- Communication style (if you prefer less blunt feedback)
- Required fetch count (default: 5+)
- TODO tracking requirements
- Logging verbosity

## Features & Benefits

### For Individual Developers
- **Consistent Code Quality**: Copilot generates code following established patterns
- **Deep Reasoning**: Extended thinking for complex problem-solving
- **Research Integration**: Automatic fetching of current best practices
- **Execution Validation**: Confidence that generated code actually works

### For Teams
- **Standardized Output**: All team members using Copilot get consistent style
- **Specification-Driven**: Clear requirements before implementation (Spec agents)
- **Quality Gates**: Enforced review and validation processes (Spec-Kitty)
- **Documentation**: Automatic logging of decisions and research

### For Legacy Projects
- **Reverse Engineering**: Extract specs from undocumented codebases
- **Modernization Planning**: Understand existing systems before refactoring
- **Knowledge Transfer**: Document tribal knowledge in specifications

## Technical Details

### Supported Languages (Coding Standards)
- Python 3.x (PEP 8, type hints, modern idioms)
- JavaScript ES6+ (Airbnb style, modern patterns)
- TypeScript 4.x+ (strict mode, advanced types)

### Agent Requirements
- **Tools**: vscode, execute, read, edit, search, web, sequentialthinking, agent, todo
- **Python Integration**: Python environment management for coding agents
- **MCP Support**: Model Context Protocol for advanced tool usage

### Timestamp Format
All agents use ISO 8601 UTC format: `YYYY-MM-DDTHH:MM:SSZ`

Generated via:
- **PowerShell**: `[System.DateTime]::UtcNow.ToString("yyyy-MM-ddTHH:mm:ssZ")`
- **Bash/sh**: `date -u "+%Y-%m-%dT%H:%M:%SZ"`

## Best Practices

### When to Use Which Agent

**Use Coding Buddy 1.3 when:**
- Working on general development tasks
- Need immediate code implementation
- Debugging existing code
- Want research-backed solutions

**Use Spec-Kitty Buddy 1.0 when:**
- Following structured development methodology
- Need rigorous requirements discovery (10+ questions)
- Working with quality gates and reviews
- Want work package management

**Use Spec Architect 1.0 when:**
- Starting new projects from scratch
- Need comprehensive architecture design
- Want detailed specifications before coding
- Brainstorming application ideas

**Use Retro-Spec Architect 1.0 when:**
- Inheriting undocumented legacy code
- Planning major refactoring or rewrites
- Need to extract domain knowledge from code
- Onboarding team to existing codebase

### Combining Agents
Recommended workflow for complex projects:
1. **Spec Architect**: Design architecture and generate specifications
2. **Spec-Kitty Buddy**: Implement features following generated specs
3. **Coding Buddy**: Handle ad-hoc coding tasks and bug fixes
4. **Retro-Spec Architect**: Document any legacy components being integrated

## Limitations

- **Agent Access**: Requires Claude 4.5/Sonnet model access through GitHub Copilot
- **Extended Thinking**: Thinking token budgets depend on model configuration
- **Fetch Tool**: Web search capabilities depend on environment setup
- **Coding Standards**: Only covers Python and JavaScript/TypeScript (extensible)

## Contributing

To add language support to coding standards:
1. Research language-specific style guides (PEP 8 equivalent)
2. Include naming conventions, formatting rules, best practices
3. Add idiomatic code examples
4. Submit pull request with clear documentation

To create new agents:
1. Follow existing agent `.md` file structure
2. Define persona, mission, and core principles
3. Specify tool requirements and workflow phases
4. Document communication style and use cases
5. Test thoroughly before submission

## License

[Specify your license here - e.g., MIT, Apache 2.0, etc.]

## Support

For issues, questions, or contributions, please [open an issue](https://github.com/jlacube/gh-copilot-tools/issues) on GitHub.

---

**Generated**: 2025-12-19T23:36:01Z  
**Version**: 1.0.0  
**Maintained By**: [Jerome Lacube]
