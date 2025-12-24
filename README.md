# GitHub Copilot Tools

A collection of GitHub Copilot customization files and agent configurations designed to enhance AI-assisted development workflows with advanced capabilities including extended thinking, research-first approaches, and specification-driven development.

## Overview

This repository provides:
- **Coding Standards**: Comprehensive guidelines for Python, JavaScript/TypeScript to help GitHub Copilot generate idiomatic code
- **Agent Configurations**: Nine specialized Claude 4.5/Sonnet agent modes optimized for different development workflows
- **Workflow Integration**: Agents designed to work together across the complete development lifecycle

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

Nine specialized agent modes covering the complete development lifecycle, all Claude 4.5/Sonnet-optimized with extended thinking capabilities.

### Agent Comparison

| Agent | Lifecycle Phase | Code Execution | Primary Tools | Best For |
|-------|----------------|----------------|---------------|----------|
| **Idea Scout 1.0** | Pre-Planning | ❌ No | web, sequentialthinking | Problem exploration, market research, solution ideation |
| **Tech Radar 1.0** | Planning | ❌ No | web, search, sequentialthinking | Technology evaluation, version tracking, stack recommendations |
| **Spec Architect 1.0** | Planning | ❌ No | web, search, sequentialthinking | Requirements discovery, architecture design, spec generation |
| **Spec Validator 1.0** | Planning | ❌ No | read, search, sequentialthinking | Specification review, completeness validation, quality assessment |
| **Spec-Kitty Buddy 1.0** | Implementation | ✅ Yes | All + execute, python | Structured development with work packages and quality gates |
| **Coding Buddy 1.3** | Implementation | ✅ Yes | All + execute, python | General development, debugging, feature implementation |
| **Retro-Spec Architect 1.0** | Documentation | ❌ No | read, edit, search, web, sequentialthinking | Legacy code analysis, reverse engineering specifications |
| **Retro-Spec Validator 1.0** | Documentation | ❌ No | read, search, sequentialthinking | Validating reverse-engineered specs against codebase |
| **Spec Steward 1.0** | Maintenance | ❌ No | read, edit, search, web, sequentialthinking | Ongoing spec maintenance, architecture validation, drift detection |

### Pre-Planning Phase

#### 1. Idea Scout 1.0
**File**: `idea-scout-1.0.agent.md`

**Description**
Problem exploration and solution ideation specialist that transforms vague ideas into validated, actionable solution approaches.

**Key Features**
- **Problem Articulation**: Transform frustrations into clear problem statements
- **Market Research**: Competitor analysis, existing solutions, gap identification
- **Solution Brainstorming**: Multiple approaches with feasibility assessment
- **MVP Definition**: Scope framing and feature prioritization
- **Idea Brief Generation**: Structured handoff document for Spec Architect
- **Batch Q&A**: 5-8 targeted questions to understand problem space

**Best Use Cases**
- Exploring whether a problem is worth solving
- Understanding market landscape before building
- Validating assumptions about user pain points
- Defining MVP scope for new ideas
- Creating idea briefs for specification phase

**Typical Output**
Generates `idea_brief.md` containing:
- Problem statement and validation
- Market analysis and competitor research
- Proposed solution approaches
- MVP scope definition
- Handoff context for Spec Architect

---

### Planning Phase

#### 2. Tech Radar 1.0
**File**: `tech-radar-1.0.agent.md`

**Description**
Technology research and evaluation specialist for data-driven stack decisions.

**Key Features**
- **Version Verification**: Latest stable versions, release dates, support status
- **Technology Comparison**: Feature comparison, pros/cons, use case fit
- **Ecosystem Assessment**: Maturity, adoption, community, documentation quality
- **Best Practices Research**: Patterns, anti-patterns, gotchas, migration paths
- **Multi-Source Validation**: Official docs, package registries, community resources

**Best Use Cases**
- Evaluating technology options for new projects
- Comparing frameworks, libraries, or tools
- Verifying version compatibility and support status
- Researching best practices for specific technologies
- Making data-driven technology stack decisions

**Research Sources**
- Official documentation and GitHub repos
- Package registries (npm, PyPI, Maven Central, etc.)
- Community resources (Stack Overflow, Reddit, HackerNews)
- Technical blogs and case studies
- Comparison sites (StackShare, ThoughtWorks Tech Radar)

---

#### 3. Spec Architect 1.0
**File**: `spec-architect-1.0.agent.md`

**Description**
Specification-focused architect for requirements discovery and comprehensive documentation generation. Does NOT execute code.

**Key Features**
- **Q&A-Driven Discovery**: 5-10 batch questions covering problem, scale, constraints, quality attributes
- **Architecture Design**: System structure, component interactions, technology selection
- **Specification Generation**: Functional specs, technical specs, data models, API contracts
- **Feature Identification**: Determines if projects should be split into multiple features
- **Technology Research**: Web-based research for optimal tech stack recommendations

**Generated Specifications**
For each feature, creates in `specs/<feature-name>/`:
- `functional_spec.md`: WHAT the feature does (requirements, user stories, workflows)
- `technical_spec.md`: HOW it's implemented (architecture, tech stack, data models)
- `api_spec.md`: API contracts, endpoints, request/response formats (if applicable)
- `testing_spec.md`: Test strategy, test cases, acceptance criteria

**Best Use Cases**
- Greenfield projects requiring comprehensive planning
- Architecture design before implementation
- Creating detailed specifications for development teams
- Converting idea briefs into actionable specs

---

#### 4. Spec Validator 1.0
**File**: `spec-validator-1.0.agent.md`

**Description**
Specification review specialist ensuring completeness, consistency, and quality before implementation begins.

**Key Features**
- **Completeness Validation**: All required sections present, questions answered
- **Consistency Checking**: No contradictions within or between documents
- **Technical Accuracy**: Correct and current technical details
- **Clarity Assessment**: Unambiguous, well-structured, implementable specs
- **Feasibility Review**: Realistic constraints and achievable architecture

**Validation Checklist**
Reviews:
- `functional_spec.md`: User stories, acceptance criteria, business rules
- `technical_spec.md`: Architecture, data models, component design
- `tech_stack.md`: Technology choices, versions, compatibility
- `implementation_plan.md`: Phases, priorities, dependencies

**Best Use Cases**
- Reviewing specs before starting implementation
- Quality assurance for Spec Architect output
- Identifying gaps in specifications
- Ensuring specs are implementable
- Team collaboration on specification quality

---

### Implementation Phase

#### 5. Spec-Kitty Buddy 1.0
**File**: `spec-kitty-buddy-1.0.agent.md`

**Description**
Implementation agent enforcing Spec-Kitty workflow methodology with mandatory quality gates and batch Q&A.

**Key Features**
- **Mandatory Batch Q&A**: Minimum 10+ questions at discovery gates (enforced, not optional)
- **Work Package Management**: WPxx format with Txxx subtasks, lane tracking
- **Quality Gates**: Constitution check, accept validation before merge
- **Spec-Kitty Workflow**: Constitution → specify → plan → research → tasks → implement → review → accept
- **Activity Logging**: All actions tracked with timestamps in `.kittify/` directory
- **Code Execution**: MANDATORY for all generated code

**Spec-Kitty Workflow Phases**
1. **Constitution Check**: Verify project principles exist before feature work
2. **Discovery**: 10+ batch questions to understand requirements
3. **Specification**: Generate comprehensive specs in `.kittify/specs/`
4. **Planning**: Create work packages with subtasks
5. **Research**: Multi-source validation with web research
6. **Implementation**: Incremental development with execution validation
7. **Review**: Code review against constitution
8. **Accept**: Final validation before merge

**Best Use Cases**
- Structured feature development with rigorous requirements
- Team projects requiring clear specifications
- Projects with quality gates and review processes
- Features requiring extensive upfront discovery

---

#### 6. Coding Buddy 1.3
**File**: `coding-buddy-1.3.agent.md`

**Description**
General-purpose coding assistant with "God of All Developers" persona featuring 200+ years of cumulative experience.

**Key Features**
- **Extended Thinking**: Leverages Claude 4.5's 64K-200K token thinking budgets
- **Research-First**: Mandatory web research from credible sources before implementation
- **Code Execution**: Zero tolerance for unexecuted code - runs everything before handoff
- **Real-time Tracking**: TODO lists and tracking files updated throughout execution
- **Timestamp Enforcement**: ISO 8601 timestamps on all entries
- **Skeptical Validation**: Fact-checks user claims before accepting them

**Communication Style**
Cold stone blunt. Direct, factual, no sugar coating. Challenges assumptions. Delivers truth over speed.

**Best Use Cases**
- Daily coding tasks across all languages/frameworks
- Bug fixes with root cause analysis
- Feature implementation with execution validation
- Code refactoring with comprehensive testing
- Ad-hoc coding without formal work packages

---

### Documentation Phase

#### 7. Retro-Spec Architect 1.0
**File**: `retro-spec-architect-1.0.agent.md`

**Description**
Reverse engineering specialist that analyzes legacy codebases and generates comprehensive specification documents. Does NOT execute or generate code.

**Key Features**
- **Codebase Discovery**: Automatic language/framework detection with user confirmation
- **Code Analysis Tools**: Extensive use of semantic_search and grep_search
- **Web Research**: Framework and pattern research using web tool for unfamiliar technologies
- **Pattern Recognition**: Identifies design patterns, anti-patterns, architectural styles
- **Requirements Extraction**: Infers user requirements from implemented features
- **Architecture Mapping**: Documents existing system structure, components, interactions
- **Specification Generation**: Creates and updates specification files directly

**Analysis Workflow**
1. **Codebase Discovery**: Scan structure, detect languages/frameworks, identify exclusions
2. **Architecture Analysis**: Map layers, identify patterns, document dependencies
3. **Feature Extraction**: Identify distinct features, understand workflows
4. **Specification Generation**: Create comprehensive docs compatible with Spec-Kitty
5. **User Confirmation**: Required at critical decision points (folder selection, module boundaries)

**Generated Specifications**
Per module/feature in `retro-specs/<feature-name>/`:
- `reverse_engineered_spec.md`: Extracted requirements and implementation details
- `architecture_analysis.md`: System structure, patterns, technology stack
- `data_model_spec.md`: Database schemas, entities, relationships
- `api_spec.md`: Existing API contracts (if applicable)

**Best Use Cases**
- Documenting undocumented legacy codebases
- Reverse engineering specifications for rewrites
- Onboarding new developers to existing projects
- Creating specs before refactoring or modernization

---

#### 8. Retro-Spec Validator 1.0
**File**: `retro-spec-validator-1.0.agent.md`

**Description**
Validation specialist ensuring reverse-engineered specifications accurately reflect actual codebase.

**Key Features**
- **Link Integrity**: Verify all code references point to valid files and line numbers
- **Coverage Analysis**: Documented vs actual files, identify gaps
- **Version Verification**: Technology versions match actual dependencies
- **Drift Detection**: Identify files modified since documentation
- **Gap Prioritization**: CRITICAL/HIGH/MEDIUM/LOW issue classification

**Validation Process**
1. Extract all markdown links from specification documents
2. Verify file existence and line number validity
3. Compare documented files vs actual codebase
4. Check dependency versions against specifications
5. Identify files modified since last spec update
6. Generate prioritized gap report

**Best Use Cases**
- Validating reverse-engineered specs against code
- Identifying outdated documentation
- Ensuring specification accuracy before handoff
- Detecting documentation drift over time
- Quality assurance for legacy documentation projects

---

### Maintenance Phase

#### 9. Spec Steward 1.0
**File**: `spec-steward-1.0.agent.md`

**Description**
Ongoing documentation maintenance system for keeping reverse-engineered specifications synchronized with evolving codebases.

**Key Features**
- **All Validator Capabilities**: Link integrity, coverage, version checking, drift detection
- **Architecture Validation**: Dependency graph analysis matching documented relationships
- **Bidirectional Traceability**: Code-to-spec and spec-to-code mapping
- **Impact Analysis**: Predict documentation updates when code changes
- **Automated Updates**: Can edit specification files to fix drift and maintain accuracy
- **Web Research**: Verify current technology versions and best practices
- **Progress Tracking**: Monitor documentation quality trends over time
- **Deep Coverage**: API-level, config, database schemas, tests, integrations

**Maintenance Workflow**
1. Execute core validation (inherited from Retro-Spec Validator)
2. Analyze import/dependency graphs for architecture fidelity
3. Build bidirectional traceability maps
4. Predict impact of code changes on documentation
5. Track historical quality metrics and trends
6. Validate API surface, config files, database schemas
7. Cross-reference test coverage with documented features

**Best Use Cases**
- Maintaining living documentation for evolving codebases
- Continuous documentation quality monitoring
- Detecting when specs need updates due to code changes
- Tracking documentation health over time
- Ensuring long-term documentation accuracy

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
   cp gh-copilot-tools/.github/agents/coding-buddy-1.3.agent.md your-project/.github/agents/
   
   # Or copy all agents
   cp gh-copilot-tools/.github/agents/*.agent.md your-project/.github/agents/
   
   # Optionally create buddy directory for agent logs
   mkdir -p your-project/.github/buddy
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

### Quick Reference: When to Use Which Agent

**Pre-Planning**
- **Idea Scout**: Vague problem → Validated solution approach

**Planning**
- **Tech Radar**: Need technology evaluation → Data-driven recommendations
- **Spec Architect**: Clear requirements → Comprehensive specifications
- **Spec Validator**: Have specifications → Quality assurance report

**Implementation**
- **Spec-Kitty Buddy**: Structured development → Work packages with gates
- **Coding Buddy**: Quick coding tasks → Immediate implementation

**Documentation**
- **Retro-Spec Architect**: Legacy codebase → Reverse-engineered specs
- **Retro-Spec Validator**: Have retro-specs → Validation report

**Maintenance**
- **Spec Steward**: Evolving codebase → Synchronized documentation

## Agent Workflow Integration

### Complete Development Lifecycle

The nine agents are designed to work together across the complete development lifecycle:

```
Pre-Planning → Planning → Implementation → Documentation → Maintenance
     ↓            ↓             ↓               ↓              ↓
Idea Scout → Spec Architect → Spec-Kitty  → Retro-Spec → Spec Steward
             Tech Radar       Coding Buddy   Architect    
             Spec Validator                  Retro-Spec
                                             Validator
```

### Workflow Scenarios

#### Scenario 1: New Greenfield Project (Full Lifecycle)

**Phase 1: Pre-Planning (Days 1-2)**
1. **Idea Scout**: Transform vague idea into validated problem statement
   - Conduct market research and competitor analysis
   - Generate idea brief with solution approaches
   - Output: `idea_brief.md`

**Phase 2: Planning (Days 3-7)**
2. **Tech Radar**: Research technology stack options
   - Evaluate frameworks, libraries, tools
   - Verify versions and compatibility
   - Output: Technology recommendations with pros/cons

3. **Spec Architect**: Design architecture and generate specifications
   - Conduct 5-10 batch questions for requirements
   - Create functional and technical specifications
   - Output: `specs/<feature>/` with comprehensive docs

4. **Spec Validator**: Review specifications before implementation
   - Validate completeness and consistency
   - Identify gaps and ambiguities
   - Output: Validation report with issues to address

**Phase 3: Implementation (Weeks 2-N)**
5. **Spec-Kitty Buddy**: Structured feature development
   - Follow Spec-Kitty workflow with work packages
   - Mandatory 10+ batch Q&A at gates
   - Execute and validate all generated code
   - Output: Implemented features in `.kittify/` structure

6. **Coding Buddy**: Ad-hoc tasks and bug fixes
   - Handle unplanned coding tasks
   - Debug and fix issues
   - Refactor and optimize code
   - Output: Executed code changes with validation

**Phase 4: Maintenance (Ongoing)**
7. **Spec Steward**: Keep specifications synchronized
   - Monitor code-to-spec drift
   - Update documentation as code evolves
   - Track documentation quality metrics
   - Output: Updated specs and quality reports

---

#### Scenario 2: Existing Undocumented Codebase

**Phase 1: Reverse Engineering (Week 1-2)**
1. **Retro-Spec Architect**: Analyze codebase and generate specs
   - Discover architecture and patterns
   - Extract features and requirements
   - Generate reverse-engineered specifications
   - Output: `retro-specs/<module>/` with comprehensive docs

2. **Retro-Spec Validator**: Validate generated specifications
   - Verify link integrity (all code references valid)
   - Check coverage completeness
   - Validate technology versions
   - Output: Validation report with gaps prioritized

**Phase 2: Enhancement (Week 3+)**
3. **Spec Architect**: Design new features based on existing architecture
   - Use reverse-engineered specs as context
   - Generate specifications for new features
   - Output: `specs/<new-feature>/` integrated with existing docs

4. **Spec-Kitty Buddy** OR **Coding Buddy**: Implement enhancements
   - Use Spec-Kitty for structured features
   - Use Coding Buddy for smaller changes
   - Output: Implemented features validated

**Phase 3: Ongoing Maintenance**
5. **Spec Steward**: Maintain documentation as code evolves
   - Detect drift between code and specs
   - Update reverse-engineered specifications
   - Track documentation health
   - Output: Synchronized documentation

---

#### Scenario 3: Quick Feature Development (No Formal Planning)

**Use Case**: Small feature or bug fix, no comprehensive planning needed

1. **Coding Buddy**: Direct implementation
   - Research-first with 5+ fetch operations
   - Generate and execute code immediately
   - Validate execution before handoff
   - Output: Working code with execution logs

**When to skip planning**: 
- Bug fixes
- Small enhancements to existing features
- Refactoring with clear scope
- Prototypes and experiments

---

#### Scenario 4: Technology Evaluation

**Use Case**: Deciding between multiple technology options

1. **Tech Radar**: Comprehensive technology research
   - Compare frameworks/libraries
   - Verify versions and compatibility
   - Research best practices and gotchas
   - Output: Data-driven recommendation report

2. **Spec Architect**: Incorporate chosen tech into specifications
   - Update technical specifications
   - Design architecture using selected stack
   - Output: Updated `technical_spec.md` and `tech_stack.md`

---

#### Scenario 5: Specification Quality Assurance

**Use Case**: Ensure specifications are ready for implementation

1. **Spec Validator**: Review forward-engineered specs
   - Validate completeness and consistency
   - Check technical accuracy
   - Ensure implementability
   - Output: Validation report with action items

2. **Retro-Spec Validator**: Validate reverse-engineered specs
   - Verify code references are accurate
   - Check coverage completeness
   - Detect documentation drift
   - Output: Validation report with prioritized gaps

---

### Workflow Decision Tree

**Starting Point: What are you building?**

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

**During Development: Which agent for what task?**

| Task | Agent | Why |
|------|-------|-----|
| Explore problem space | Idea Scout | Market research, solution brainstorming |
| Research technologies | Tech Radar | Version tracking, ecosystem assessment |
| Create specifications | Spec Architect | Architecture design, comprehensive docs |
| Review specifications | Spec Validator | Quality assurance before implementation |
| Structured development | Spec-Kitty Buddy | Work packages, quality gates, batch Q&A |
| Quick coding tasks | Coding Buddy | Immediate implementation, execution validation |
| Document legacy code | Retro-Spec Architect | Reverse engineering, pattern recognition |
| Validate legacy docs | Retro-Spec Validator | Link integrity, coverage analysis |
| Maintain documentation | Spec Steward | Drift detection, ongoing synchronization |

---

### Agent Handoffs

Agents are designed to produce outputs that serve as inputs for the next agent:

1. **Idea Scout → Spec Architect**
   - Input: Vague idea or problem
   - Output: `idea_brief.md` with problem statement, market analysis, solution approaches
   - Handoff: Spec Architect uses idea brief as context for specifications

2. **Tech Radar → Spec Architect**
   - Input: Technology evaluation request
   - Output: Technology comparison and recommendation
   - Handoff: Spec Architect incorporates tech stack into technical specifications

3. **Spec Architect → Spec Validator**
   - Input: Project or feature concept
   - Output: Comprehensive specifications in `specs/<feature>/`
   - Handoff: Spec Validator reviews for completeness before implementation

4. **Spec Validator → Spec-Kitty Buddy**
   - Input: Specifications to validate
   - Output: Validation report with gaps identified
   - Handoff: Spec-Kitty Buddy implements validated specifications

5. **Retro-Spec Architect → Retro-Spec Validator**
   - Input: Legacy codebase
   - Output: Reverse-engineered specifications in `retro-specs/<module>/`
   - Handoff: Retro-Spec Validator checks accuracy against actual code

6. **Retro-Spec Validator → Spec Steward**
   - Input: Reverse-engineered specifications
   - Output: Validation report with issues prioritized
   - Handoff: Spec Steward sets up ongoing maintenance and monitoring

7. **Any Agent → Coding Buddy**
   - Input: Ad-hoc coding request
   - Output: Implemented and executed code
   - Handoff: No formal handoff, immediate task completion

---

### When NOT to Use Multiple Agents

Direct to **Coding Buddy** for:
- Simple bug fixes with clear root cause
- Small refactoring with obvious scope
- Quick prototypes or experiments
- Single-file changes
- Immediate coding questions

Direct to **Spec Architect** (skip Idea Scout) when:
- Requirements are already clear
- Problem validation is complete
- Time-sensitive projects

Direct to **Spec-Kitty Buddy** (skip Spec Architect) when:
- Specifications already exist
- Following existing patterns
- Extending existing features

## Limitations

- **Agent Access**: Requires Claude 4.5/Sonnet model access through GitHub Copilot (Pro, Pro+, Business, or Enterprise plans)
- **Extended Thinking**: Thinking token budgets depend on model configuration
- **Web Tool**: Web search capabilities depend on environment setup
- **Coding Standards**: Currently covers Python and JavaScript/TypeScript (extensible)
- **Agent Count**: Repository includes 9 agents; choose relevant ones for your workflow

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

MIT License

Copyright (c) 2025 Jerome Lacube

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Support

For issues, questions, or contributions, please [open an issue](https://github.com/jlacube/gh-copilot-tools/issues) on GitHub.

---

**Last Updated**: 2025-12-24  
**Version**: 2.0.0  
**Maintained By**: Jerome Lacube
