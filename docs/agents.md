# Agent Configurations

Nine specialized agent modes covering the complete development lifecycle, all Claude 4.5/Sonnet-optimized with extended thinking capabilities.

## Agent Comparison

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

---

## Pre-Planning Phase

### 1. Idea Scout 1.0
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

## Planning Phase

### 2. Tech Radar 1.0
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

### 3. Spec Architect 1.0
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

### 4. Spec Validator 1.0
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

## Implementation Phase

### 5. Spec-Kitty Buddy 1.0
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

### 6. Coding Buddy 1.3
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

## Documentation Phase

### 7. Retro-Spec Architect 1.0
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

### 8. Retro-Spec Validator 1.0
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

## Maintenance Phase

### 9. Spec Steward 1.0
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

---

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
All agents maintain detailed logs (where applicable) in `.github/buddy/` directory:
- `thinking_log.md`: All reasoning processes with timestamps and thinking budgets
- `research_log.md`: All fetch operations, queries, URLs, findings with timestamps
- `execution_log.md`: All code execution results with timestamps
- `progress.md`: Real-time TODO lists updated throughout execution

**Note**: The buddy directory is automatically created by agents and is typically gitignored.

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
